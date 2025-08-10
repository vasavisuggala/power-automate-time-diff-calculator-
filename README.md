# Power Automate Time Difference Calculator

![Power Automate](https://img.shields.io/badge/Microsoft%20Power%20Automate-Flow-blue?logo=power-automate&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Active-success)
![Platform](https://img.shields.io/badge/Platform-Microsoft%20Cloud-lightblue)

A Microsoft Power Automate flow that calculates the time difference between two timestamps and performs automated actions such as reminders, escalations, or SLA tracking. Ideal for task monitoring, process automation, and scheduled notifications.


# Features

	•	Calculates difference in hours and minutes
	•	Works with any data source (SharePoint, Dataverse, Excel, etc.)
	•	Triggers reminders or escalations based on thresholds
	•	Useful for SLA monitoring and process tracking
	•	100% customizable without third-party connectors


# Use Cases

	•	Send reminders before deadlines or events
	•	Trigger escalation if tasks are overdue
	•	Track SLA compliance for support tickets
	•	Schedule follow-up actions after a defined time gap




# Pseudo Flow Logic

```
START
  GET tickStart ← Start time from data source
  GET tickEnd   ← Current time (utcNow()) OR stored end time

  diffMinutes = (tickEnd - tickStart) in minutes
  diffHours   = diffMinutes ÷ 60
  modMinutes  = diffMinutes % 60

  result = "{diffHours} hours {modMinutes} minutes"

  IF diffMinutes > threshold
      → Trigger escalation/reminder
  ELSE
      → Wait or schedule next check
END

```




# Expressions Used

```
// Calculate difference in minutes
div(
  sub(ticks(variables('tickEnd')), ticks(variables('tickStart'))),
  600000000
)

// Hours from minutes
int(div(variables('diffMinutes'), 60))

// Remaining minutes after hours
mod(variables('diffMinutes'), 60)

```




# Example Scenarios

-	If the time difference is ≥ 48 hours since a request was created → send an escalation email to the manager.
- If the difference is exactly 30 minutes before an event → send a Teams reminder.

 

# Setup Instructions
1.	Create a new flow in Power Automate.
2.	Add variables:
	•	tickStart → Start timestamp from data source.
	•	tickEnd → Current timestamp (utcNow()) or stored end time.
3.	Add calculation steps for minutes, hours, and modulus.
4.	Store final result in result variable.
5.	Add conditional actions (e.g., send email, post Teams message).
6.	Test the flow with sample timestamps.



# License

This project is licensed under the MIT License — free for personal and commercial use.

# Credits

[**Vasavi**](https://github.com/vasavisuggala)  
[**Dileep**](https://github.com/dileepsuggala)  
[**Sai**](https://github.com/msdev777)  




