**
# 🚀 IP Monitoring Script v9 - README

Welcome to **IP Monitoring Script v9** – a lightweight yet powerful tool to monitor the stability of your network in real-time, with instant Telegram alerts. Ideal for sysadmins, engineers, or anyone who wants to stay informed about network health.

---

## ✨ What's New in Version 9?

✅ **Instant DEGRADED alerts** for packet loss ≥ 20% (no 4-minute delay)  
📉 **Alerts are only sent if packet loss changes**, avoiding repeated messages  
📡 **Automatic MTR snapshot** during DOWN status for easy troubleshooting  
🔄 **More informative RECOVERED messages** with downtime duration and last loss  
🧹 **Weekly log cleanup** to keep the system lightweight and clean

---

## ⚙️ Key Configuration

- `TARGETS`: List of monitored IPs with friendly names (e.g., GoogleDNS1, CloudFlare)
- `TELEGRAM_BOT_TOKEN` & `TELEGRAM_CHAT_ID`: For sending alerts to Telegram
- `LOG_DIR`: Log file directory (default: `/var/log/ip-monitor`)
- `PING_COUNT`: Number of ping packets per check (default: 10)
- `RETENTION_DAYS`: Days to keep logs before cleanup (default: 7)

---

## 🔔 Notification System

- 🟥 **DOWN**  
  - Sent once when target is DOWN  
  - Includes MTR snapshot (`--report`) for trace diagnostics

- 🟨 **DEGRADED** (Packet Loss ≥ 20%)  
  - Triggered instantly  
  - Only resent if packet loss value changes

- ✅ **RECOVERED**  
  - Sent when the state returns to UP  
  - Includes downtime duration and last packet loss info

---

## 📁 Log Structure

- `downtime.log` → History of DOWN events  
- `degraded.log` → History of DEGRADED states  
- `uptime.log` → History of recoveries (UP)  
- `debug.log` → Ping output and debug info  
- `mtr-*.log` → MTR snapshots from DOWN events  

> Logs are automatically cleaned up every Sunday at 03:00 if older than 7 days.

---

## ⏱ Recommended Cronjob

Run every 2 minutes by adding this to your crontab:

```bash
*/2 * * * * /path/to/your/script.sh
```

---

## 📌 Tips & Notes

- Ensure `curl` and `mtr` are installed on your system
- Run the script with proper permissions (`sudo` if needed)
- Use a VPS or server with stable uptime for best monitoring results

---

## 💬 Need Help?

Contact your infra team or script maintainer for Telegram bot integration and support.

---

Happy monitoring! 📡🔧  
_This script is designed for maximum reliability and performance._

**
