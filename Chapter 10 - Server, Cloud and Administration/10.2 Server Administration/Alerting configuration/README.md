# Alerting configuration
**Alerting Configuration in Tableau Cloud**

**Introduction**
Tableau Cloud provides alerting features for data-driven notifications and subscription-based content updates. These tools allow users to receive automated notifications when data changes or when new content is published. This guide covers the two primary methods: Data Driven Notifications and Subscriptions.

**Data Driven Notifications**
Data Driven Notifications allow users to set alerts on specific data points in a view. The system monitors the data and sends an alert when conditions are met.

**Core Function**
Users can subscribe to a single mark or a header in a view. They receive an alert when the underlying data value crosses a user-defined threshold.

**Configuration Process**
*   Users open a published view on Tableau Cloud.
*   They click the alert (bell) icon on the toolbar.
*   The user selects "Add Alert" on a specific data mark or axis header.
*   A configuration pane opens on the right side of the screen.

**Alert Settings**
Users define these parameters:
*   **Condition**: Choose when the alert triggers.
    *   "When value meets a condition" (e.g., is greater than 10).
    *   "When value changes" (any change in the data point).
    *   "When data is refreshed" (triggers on each successful refresh).
*   **Trigger Threshold**: For condition-based alerts, set the numerical threshold (e.g., >, <, =, >=, <=).
*   **Notification Frequency**: Choose how often to receive the alert.
    *   "Once per data change" sends one alert when the condition is first met.
    *   "Each time condition is met" sends repeated alerts for each refresh cycle where the condition holds true.
*   **Delivery Method**: Select email or mobile push notification via the Tableau Mobile app.

**Management**
*   Users manage their alerts in "My Alerts" under their account settings.
*   Administrators can see all alerts on the site in the Admin area under "Subscriptions and Alerts."

**Limitations**
*   Alerts require a live connection to the underlying data source or a regularly refreshed extract.
*   The view author must enable alerts for the worksheet.
*   Alerts only work on views with a single, discrete data point.

**Subscriptions**
Subscriptions allow users to receive scheduled snapshots of an entire view or workbook via email.

**Core Function**
Users receive a static image of a view or a link to a workbook delivered on a set schedule.

**Configuration Process**
*   Users open a view or workbook on Tableau Cloud.
*   They click the subscribe (bell or envelope) icon.
*   They select the subscription frequency: daily, weekly, or monthly.
*   The user chooses the delivery time and format.

**Subscription Settings**
*   **Content**: Subscribe to a specific view or an entire workbook.
*   **Schedule**: Set daily, weekly, or monthly delivery.
*   **Attachment**: Choose to receive the view as an embedded image or a PDF attachment.
*   **Filters**: Some subscriptions allow users to set a personalized filter for the data they receive.

**Management**
*   Users manage personal subscriptions in "My Subscriptions."
*   Site Administrators can view and manage all subscriptions from the Admin area.

**Key Differences Between Alerts and Subscriptions**
*   **Trigger**: Alerts are data condition-based. Subscriptions are time-based.
*   **Content**: Alerts notify about a specific data point change. Subscriptions deliver a full view image.
*   **Use Case**: Use alerts for monitoring key metrics. Use subscriptions for regular report distribution.

**Administrative Controls**
Site Administrators have oversight tools for alerting.

**Access and Permissions**
*   Site Administrators can disable the "Alerts" or "Subscriptions" feature site-wide via Site Settings.
*   Workbook owners can disable alerts for their specific workbooks.
*   User ability to create alerts depends on their license type and permissions on the view.

**Monitoring**
*   The "Subscription Activity" Admin view lists all active alerts and subscriptions.
*   Admins can see the view, recipient, schedule/condition, and status.

**Best Practices for Configuration**

**For View Creators**
*   **Optimize Data Sources**: Ensure data sources for alerting views use extracts or have fast live connections for reliable evaluation.
*   **Simplify Views**: Design clear, single-point views for critical metrics to make alert setup intuitive for users.
*   **Communicate**: Inform users which views are configured for alerts and what the key metrics mean.

**For Administrators**
*   **Set Governance**: Establish guidelines for what types of data should use alerts to prevent notification overload.
*   **Monitor Volume**: Use the Admin view to monitor the total number of alerts. A very high count may indicate poorly designed thresholds.
*   **Audit Regularly**: Periodically review the "Subscription Activity" view to deactivate alerts on deprecated views or for inactive users.
*   **Leverage Defaults**: Configure default schedules for subscriptions to standardize delivery times across the site.

**Technical Considerations**

**Data Refresh Dependency**
*   Alerts only evaluate data during a scheduled extract refresh or when a live connection is queried.
*   Subscriptions capture the view state at the scheduled time, which may depend on extract schedules.

**Failure Handling**
*   If a data source fails to refresh, dependent alerts will not trigger.
*   Subscription emails will not send if the view errors at the scheduled delivery time.
*   System errors are logged for administrator review.

**Conclusion**
Alerting in Tableau Cloud provides two main tools: Data Driven Notifications for threshold-based data alerts and Subscriptions for scheduled report delivery. Effective use requires understanding their distinct functions and configuration options. Administrators should monitor usage and establish light governance to maintain system performance and user relevance. Properly configured, these features turn static dashboards into proactive communication tools that drive timely business decisions.
