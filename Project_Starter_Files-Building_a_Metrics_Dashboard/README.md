**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation

To verify the monitoring setup, the kubectl commands were executed to display the running pods and services for all components. The following screenshot captures the output: 

verify_the_monitoring_installation.png

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.

The screenshot below shows the Grafana home page after logging in

setup_the_jaeger_and_prometheus_source.png

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

The screenshot below shows a Grafana dashboard with Prometheus as the data source:

create_a_basic_dashboard.png


## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

Service Level Indicators (SLIs) are precise, measurable metrics that help assess whether a system meets its Service Level Objectives (SLOs). For the SLOs of monthly uptime and request response time, the SLIs can be defined as follows:

Monthly Uptime:
What It Measures: The percentage of time during a month that the system is fully operational and accessible to users.
How It’s Calculated: Uptime is measured by tracking periods of availability versus total possible uptime within the month. Downtime caused by outages, maintenance, or failures directly affects this metric.
Example: For an SLO requiring 99.95% uptime, the SLI would track actual uptime to ensure the service remains available for at least 99.95% of the month.

Request Response Time:
What It Measures: The time it takes for the system to respond to a user's request, from initiation to completion.
How It’s Calculated: Monitors the time taken for a sample of requests and reports metrics such as the median, average, or percentile response times (e.g., 95th percentile).
Example: For an SLO stating that 95% of requests must have a response time under 200 milliseconds, the SLI evaluates request logs to confirm compliance with this target.
These SLIs are vital for tracking service performance and ensuring the system aligns with the agreed-upon objectives. They provide clear, actionable data to detect and address potential issues early.

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

It is essential to understand the purpose of measuring specific metrics for our customers to ensure their experience aligns with expectations. Below are five Service Level Indicator (SLI) metrics, along with detailed explanations of their significance:
1. Availability
Description: Measures the percentage of time the system is operational and accessible to customers.
Why It Matters: Ensures customers can reliably use the service when needed. High availability builds trust and reduces customer churn.
Example Metric: Uptime Percentage ((Total Uptime / Total Time) * 100).
2. Latency
Description: Measures the time taken to process a request, from initiation to response.
Why It Matters: Low latency enhances user experience, especially for real-time or high-frequency interactions.
Example Metric: 95th Percentile Response Time (tracks the upper boundary of response times for most requests).
3. Error Rate
Description: Measures the percentage of failed requests or operations compared to the total number of requests.
Why It Matters: A high error rate can indicate system instability, directly impacting customer satisfaction.
Example Metric: (Total Failed Requests / Total Requests) * 100.
4. Throughput
Description: Measures the volume of requests or transactions processed by the system over a given period.
Why It Matters: Throughput indicates the system's capacity to handle customer demand, ensuring scalability during peak loads.
Example Metric: Requests Per Second (RPS) or Transactions Per Minute (TPM).
5. Durability
Description: Measures the reliability and accuracy of data storage and retrieval within the system.
Why It Matters: Ensures data integrity and prevents data loss, critical for customer trust and regulatory compliance.
Example Metric: Data Loss Rate ((Total Data Loss / Total Data Stored) * 100).
These metrics provide actionable insights into system performance, enabling teams to optimize service delivery and meet customer expectations effectively.


## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

Frontend and Backend Uptime Dashboard:
The screenshot below displays a dashboard that measures the uptime of both the frontend and backend services.

create_a_dashboard_to_measure_our_SLIs_frontend_backend_uptime_dashboard.png

Error Monitoring Dashboard:
The screenshot below showcases a dashboard tracking 40x and 50x errors over a 24-hour period.

create_a_dashboard_to_measure_our_SLIs_error_monitoring_dashboard.png

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

Jaeger Span Screenshot:
The screenshot below shows a Jaeger span that captures the backend service's processes for tracing and performance monitoring.
tracing_our_flask_app_jaeger_span.png

Trace and Span Code Screenshot:
The screenshot below highlights the Python code used to implement Jaeger tracing on the backend service, including the creation of spans for detailed process monitoring.
tracing_our_flask_app_sample_python_file.png


## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

The following is a screenshot showing Jaeger integrated into the current Grafana dashboard:
jaeger_in_dashboards.png

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name: Michelle
Date: January 3rd, 2025
Subject: Error Report for 500 and Latency Issues
Affected Area: Trial Service
Severity: High
Description:
We are encountering intermittent HTTP 500 errors and prolonged latency in the Trial Service, adversely affecting the user experience. The root cause appears to originate from specific operations in the Trial Service, as observed in the Jaeger traces. Attached below is a screenshot of the tracer span that highlights the specific segment of the service where the issue is occurring. This demonstrates how Jaeger is being utilized to pinpoint errors effectively.

Please investigate and resolve this issue as soon as possible.

Attachment: Screenshot of the tracer span showing the error.
report_errors.png

## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

Objective: Define four Service Level Indicators (SLIs) to measure the success of an SLO guaranteeing 99.95% uptime per month for the application.

SLIs to Measure Success:

Availability:
Definition: The percentage of time the application is accessible and operational for end-users.
Measurement: (Total Uptime / Total Time) * 100
Why It Matters: Ensures the application meets the uptime SLO by tracking its operational state.

Error Rate:
Definition: The percentage of failed requests or operations relative to total requests.
Measurement: (Total Failed Requests / Total Requests) * 100
Why It Matters: A high error rate could indicate downtime or service degradation, directly affecting uptime.

Response Time (Latency):
Definition: Measures the time it takes to process a user request.
Measurement: 95th or 99th percentile response time for requests over a specific period.
Why It Matters: Excessive latency can render the application effectively unavailable for users, even if technically "up."

Service Health Checks:
Definition: Periodic checks to verify the health of key application components and endpoints.
Measurement: Percentage of successful health check responses during the monitoring period.
Why It Matters: Regular health checks ensure components are functioning as expected, contributing to overall uptime.

These SLIs provide comprehensive insights into the application's performance and ensure the 99.95% uptime goal is effectively monitored and achieved.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

Objective: Define 2-3 Key Performance Indicators (KPIs) to accurately measure the defined SLIs and SLOs.

KPIs:

Uptime Percentage
Definition: Tracks the total uptime of the application as a percentage of total time in a given period (e.g., monthly).
Why This KPI?: Directly reflects the SLO of 99.95% uptime and provides an overarching view of application availability. It is critical for maintaining service reliability and customer trust.

Error Rate Trend
Definition: Measures the percentage of failed requests or operations and tracks changes over time.
Why This KPI?: A decreasing error rate indicates improvement in system stability, while an increasing trend may signal potential issues affecting uptime or performance.

95th Percentile Response Time
Definition: Captures the latency experienced by 95% of users, excluding extreme outliers.
Why This KPI?: Ensures that most users have a seamless experience by measuring response time, which directly impacts perceived uptime and usability.

These KPIs will form the foundation of the dashboard, offering actionable insights into whether the application meets its SLOs and highlighting areas for optimization.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  

The dashboard shown in the screenshot effectively captures the key metrics to evaluate the defined KPIs, SLIs, and SLOs for the system's performance. Below are the graphs and their purposes:

Response Code Graph:
Displays the frequency of HTTP response codes, including 40x (client errors) and 50x (server errors), over the selected time range.
Helps in identifying patterns of errors and assessing system reliability.

Response Time Graph:
Plots the average response time (in milliseconds) for the system over a 3-hour period.
This metric ensures the SLO for request response time is met and highlights latency trends.

Uptime Percentage Graph:
Shows the percentage uptime of the frontend and backend services.
Tracks service availability and ensures adherence to the monthly uptime SLO.

This comprehensive dashboard provides a real-time view of system performance and enables proactive monitoring to maintain service reliability and quality.
final_dashboard.png

