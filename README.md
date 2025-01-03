Problem Statement 2: Script Implementation
Objective 1: System Health Monitoring
How It Works:
  Thresholds:
    Adjust the CPU, memory, and disk usage thresholds in the script to suit your needs.
  
  Log Output:
    The script logs any violations (e.g., CPU usage > 80%) into /var/log/sys_health.log.

  Automate Execution:
    Add the script to cron for periodic execution:

     crontab -e

Add the following line to run the script every 5 minutes:
      
      */5 * * * * /path/to/sys_health.sh

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

Objective 2: Log File Analyzer
  Log Format Assumption:
      -The script assumes the logs follow a standard format like Apache’s access log

      127.0.0.1 - - [02/Jan/2025:10:00:00 +0000] "GET /index.html HTTP/1.1" 200 2326

Detailed Breakdown:
  -Extracting 404 Errors: The script identifies all lines containing 404 and counts them.
  -Most Requested Pages: It extracts the requested pages (e.g., /index.html) and counts their frequency.
  -Most Active IPs: The script identifies IP addresses making the most requests.

Enhancements:
  -Output the analysis to a file
  
     with open("log_analysis_report.txt", "w") as report:
    report.write(f"Number of 404 errors: {len(errors_404)}\n")
    report.write("Most requested pages:\n")
    for page, count in most_requested:
        report.write(f"{page}: {count} requests\n")
    report.write("Most active IPs:\n")
    for ip, count in most_active_ips:
        report.write(f"{ip}: {count} requests\n")


Automation:
  -Schedule this script using cron for periodic analysis of logs.


////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


1. Automating System Health Monitoring
  -Integrating email alerts using tools like mail or sendmail.
  -Explaining how to set up a log rotation mechanism for /var/log/sys_health.log.

2. Automating the Backup Script
  -Setting up SSH keys for secure file transfer to a remote server.
  -Configuring the script to upload backups to cloud storage (e.g., AWS S3, Google Drive).

3. Improving the Log File Analyzer
  -Customizing the script to support non-standard log formats.
  -Extending the script to generate graphical reports (e.g., using matplotlib in Python).

4. Application Health Checker
  -Adding functionality to send real-time alerts if the application goes down.
  -Extending the script to handle multiple URLs or APIs in one execution.

