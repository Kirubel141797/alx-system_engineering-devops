Postmortem: Website Outage Due to Database Overload
Issue Summary
On March 3, 2024, from 14:00 to 16:30 EST, our primary web service experienced a 2.5-hour outage impacting approximately 35% of our user base. During this period, users experienced slow response times and intermittent downtime. The service affected was our user data retrieval system, which is crucial for user login and information display. The root cause was identified as an overloaded database server due to an unexpected surge in user traffic, coupled with inefficient query handling.

Timeline
14:00 EST - Initial reports of slow website performance were detected by our automated monitoring system.
14:05 EST - The engineering team was alerted by the monitoring system notification.
14:10 EST - Preliminary investigation suggested a database performance bottleneck. CPU usage on the database server was at 95%.
14:20 EST - Efforts to optimize database queries were initiated but didn't yield the expected improvement.
14:45 EST - A deeper analysis revealed a large number of redundant queries being generated due to a recent code deployment.
15:00 EST - The issue was escalated to the senior database administrator and the site reliability engineering (SRE) team.
15:30 EST - Misleading investigation path regarding potential DDoS attack was ruled out.
15:45 EST - The problematic code deployment was identified as the primary cause of the additional load.
16:00 EST - A rollback of the recent deployment was executed.
16:15 EST - Database performance began to normalize, and website response times improved.
16:30 EST - Full service was restored, and monitoring confirmed the resolution.
Root Cause and Resolution
The outage was primarily caused by an inefficiently designed feature deployment that led to an excessive number of database queries. This surge overwhelmed the database server, leading to high CPU usage and slow response times. The situation was exacerbated by a recent increase in active users, which was not accounted for in the service's capacity planning.

The issue was resolved by rolling back the recent deployment that contained the inefficient code. Following the rollback, the database server's load returned to normal levels, and the web service's performance stabilized.

Corrective and Preventive Measures
To prevent future occurrences of this issue, we have identified several areas for improvement:

Review and Optimization of Code Deployment Processes: Implement stricter code review processes with a focus on performance implications, especially for database-intensive features.
Enhanced Database Monitoring: Expand our monitoring capabilities to include more granular metrics on query performance and frequency.
Capacity Planning: Revise our capacity planning processes to accommodate unexpected spikes in user traffic, with a particular focus on scaling database resources.
Training and Awareness: Conduct training sessions for the development team on best practices for database efficiency and query optimization.
Tasks to Address the Issue:

Patch and optimize database servers to handle higher loads.
Add automated alerts for unusual database query patterns.
Implement a more rigorous pre-deployment testing phase that includes load testing.
Schedule a series of developer training sessions on efficient database usage and query optimization.
This incident highlighted the need for thorough testing and review of code changes, especially those that could significantly impact system performance. By addressing these areas, we aim to improve our resilience to traffic spikes and prevent similar outages in the future.

User
1. Make people want to read your postmortem
#advanced
We are constantly stormed by a quantity of information, it’s tough to get people to read you.

Make your post-mortem attractive by adding humour, a pretty diagram or anything that would catch your audience attention.

