<img width="212" alt="Screenshot 2022-07-21 at 01 02 03" src="https://user-images.githubusercontent.com/29555611/180102491-dd90a9ed-fd39-41bb-a609-e186e82c10bf.png">

# Blockpilabs HyperNode-Polygon monitoring
This is one-line bash script to get node_exporter-prometheus-grafana + grafana dashboard installed for monitoring **HyperNode-Polygon Node**.

Testnet: https://testnet-docs.blockpi.io/guide-for-operators/testnet-1

## Prerequisite:
 - It is assumed that there is no node_exporter/prometheus/grafana installed
 - It is assumed ports: 9100, 9090, 3000 are not in use
 - You need to make sure that metrics enabled for both Heimdall and Bor:
   - change `prometheus` flag to `true` in the `config.toml` 
    ```
    vi ~/.heimdalld/config/config.toml
    ```
   - in `polygon-bor` service file add keys:
    ```
    --metrics --pprof --pprof.port 7071 --pprof.addr '0.0.0.0'
    ```


## How to use:
On HyperNode-Polygon server run
```
wget -q -O blockpi-monitoring-installer.sh https://raw.githubusercontent.com/davaymne/blockpilabs-hypernode-polygon-monitoring/main/blockpi-monitoring-installer.sh && chmod +x blockpi-monitoring-installer.sh && sudo /bin/bash blockpi-monitoring-installer.sh
```
Go to you web browser and enter:
```
http://YOUR-NODE-IP:3000/
```
Use Grafana default credentials:
 - User: admin
 - Pass: admin
 
 ## Optional: Configure Alert Notification
 
 ### Set up Telegram Bot 
 
 - Telegram bot
@BotFather - https://core.telegram.org/bots (https://core.telegram.org/bots#6-botfather)

 - Create Telegram group and add your bot into the group to receive notifications from bot in this group 
 
 ### Set up Alerts Contact Point
 
 - Go to your grafana and add Contact Point
<img width="1251" alt="Screenshot 2022-07-21 at 00 34 24" src="https://user-images.githubusercontent.com/29555611/180100288-c480d49a-4031-485b-a5e8-f512f070fd5e.png">

 
 Official website: https://grafana.com/docs/grafana/latest/alerting/contact-points/create-contact-point/
 
### Set up Alert Rule for Polygon node

 - Go to Grafana -> HyperNode dashboard -> Blocks per min chart and select `Edit`
 
<img width="514" alt="Screenshot 2022-08-26 at 00 52 14" src="https://user-images.githubusercontent.com/29555611/186788615-99bd7852-d564-4072-8c7d-31efec7f9c7c.png">

 - Click `Create Alert Rule from this panel`
 
 <img width="1011" alt="Screenshot 2022-07-21 at 00 46 07" src="https://user-images.githubusercontent.com/29555611/180101210-c3552803-28cd-4818-93a2-30747b608d66.png">

 - Configure Alert Rule as per screenshots below
 
<img width="1366" alt="Screenshot 2022-08-26 at 00 54 27" src="https://user-images.githubusercontent.com/29555611/186788908-9d30b963-1f75-4d19-b02a-e58fc8327913.png">

<img width="1354" alt="Screenshot 2022-08-26 at 00 55 17" src="https://user-images.githubusercontent.com/29555611/186788918-c65d2fbb-a4bd-45a2-ba5a-b030fe79c467.png">

<img width="1367" alt="Screenshot 2022-08-26 at 00 55 39" src="https://user-images.githubusercontent.com/29555611/186788928-a45aaa03-c612-4d2d-befe-52a41d141dcd.png">

Official website: https://grafana.com/docs/grafana/latest/alerting/alerting-rules/create-grafana-managed-rule/
