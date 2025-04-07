# AWS CloudWatch Demo - Real-time Monitoring & Alerts 🚨☁️

This project demonstrates how to monitor an EC2 instance using AWS CloudWatch, simulate a CPU spike, and trigger an alarm with email notifications.

---

## 📋 Steps Covered:

### ✅ 1. EC2 Monitoring with CloudWatch
- Enabled detailed monitoring on EC2 (1-minute interval).
- Viewed CPU metrics in **CloudWatch > Metrics > EC2 > Per-Instance Metrics**.

### 🧪 2. Simulating a CPU Spike
- Created `cpu_spike.py` to simulate high CPU usage (up to 99%).
- Observed the spike in CloudWatch metrics dashboard.

### 🚨 3. Creating an Alarm with SNS Notification
- Set up an alarm to trigger when CPU > 50% for 1 minute.
- Created an **SNS topic** to send email notifications.
- Verified alert by re-running the spike script.

---

## 🔧 Script: `cpu_spike.py`
```python
import time

def simulate_cpu_spike(duration=30, cpu_percent=80):
    print(f"Simulating CPU spike at {cpu_percent}%...")
    start_time = time.time()
    target_percent = cpu_percent / 100
    total_iterations = int(target_percent * 5_000_000)

    for _ in range(total_iterations):
        result = 0
        for i in range(1, 1001):
            result += i

    elapsed_time = time.time() - start_time
    remaining_time = max(0, duration - elapsed_time)
    time.sleep(remaining_time)

    print("CPU spike simulation completed.")

if __name__ == '__main__':
    simulate_cpu_spike(duration=30, cpu_percent=80)
