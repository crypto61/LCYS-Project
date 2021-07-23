End of Course Assessment Project for LYCS.

## Presents python code for adressing one security issue as presented in unit 9 essay (Queen's Medical Centre)
## Comments on each section within code. Run results are in file: lcysproject_proof_of_operation.txt.
## References used for code syntax verification are at bottom of code seection.

### Begin lcysproject.py

### LYCS Module Assessment - Use python to create code to address one issue identified
### in module 9 essay - Queen's Medical Centre, Secure web-based appointment system.
### Selected issue is human error in forgetting to update firewall security patches.
### Code intends to address the issue by automating a daily script to examine the latest patch date for 2 firewalls 
### generate warning messages to a log file and send an email to staff.

## Approach: 
## Query last patch date from firewall system file
## Determine patch expiration date based on a manadatory 30 day refresh cycle.
## Compare today's date to expiration date for each firewall.
## Print status of each firewall to console for confirmation
## If firewall patch is out of date, send log warning msg to "file.log"

## Originally included code to also send an email to CISO and security tech. 
## But this only worked without error when I included my real email server details including passwords.
## So I have removed the email code to provide a clean run output file free of errors and easy to see proof of concept.
## However to document learning experience that went into that effort, I am including a copy of the code 
## (with generic email info) for review in README_emailcode.txt.


from datetime import date, timedelta
today = date.today()

# representing the patch date of firewall 1 pulled (simulated) from firewall 1 system file.
p1 = date (2021, 7, 15) 
# representing the patch date of firewall 2 pulled (simulated) from firewall 2 system file.
p2 = date (2021, 5, 15)

# This calculates the expiration date for security patch upgrade based on 30 days maximum life of patch.
exp1 = (p1 + timedelta(days = 30))
exp2 = (p2 + timedelta(days = 30))

# Prints date info to console to confirm process has completed and is in expected range.
# contains a string description and variable output

print ()
print ("today's date is", (today))
print ()
print ("firewall 1 patch date is", (p1))  
print ()
print ("firewall 2 patch date is", (p2))
print ()  
print ("Firewall 1 expiration date is", (exp1))
print ()
print ("Firewall 2 expiration date is", (exp2))
print ()

## Enables logging

import logging

# Creates a custom logger
logger = logging.getLogger(__name__)

# Creates handlers (in this case only file handlers as console output is called directly from the code)
# file handler creates file.log and writes event data as specified in msg creation throughout code. logger.warning("string")

f_handler = logging.FileHandler('file.log')
f_handler.setLevel(logging.WARNING)

# Creates formatters and add it to handlers

f_format = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
f_handler.setFormatter(f_format)

# Add handlers to the logger as defined in 2 steps above

logger.addHandler(f_handler)


## provides operations to compare security patch exiration date to today's date and generate output process accordingly. 
# variables used have been defined in first section

if today < exp1:
  print ("Patch status of firewall 1 is current", (today))
  print ()
elif today > exp1:
  print ("PATCH STATUS OF FIREWALL 1 IS OUT OF DATE AND REQUIRES IMMEDIATE ATTENTION", (today))
  logger.warning("PATCH STATUS OF FIREWALL 1 IS OUT OF DATE AND REQUIRES IMMEDIATE ATTENTION")

  
if today < exp2:
  print ("Patch status of firewall 2 is current", (today))
  print ()
elif today > exp2:
  print ("PATCH STATUS OF FIREWALL 2 IS OUT OF DATE AND REQUIRES IMMEDIATE ATTENTION", (today))
  logger.warning("PATCH STATUS OF FIREWALL 1 IS OUT OF DATE AND REQUIRES IMMEDIATE ATTENTION")

## References:

# General, I followed my own original code outline (attached). For style and syntax guide I referred to the following resources:
	Python 3.9.6 documentation available from docs.python.org/3/ [accessed july 2021]
	PEP 8 -- Style Guide for Python Code available from python.org/dev/peps/pep-0008/ [accessed July 2021]

# General, I discovered some of my resources were based on a different version of python and would result in an error. For determining source of the error I used https://www.tutorialsteacher.com/python/error-types-in-python [accessed July 2021]

# Timedelta syntax help for adding specific number of days to a given date: https://www.geeksforgeeks.org/python-datetime-timedelta-function/ [Accessed July, 2021]

# For error resolution with a logging configuration line: https://realpython.com/python-logging/#the-logging-module [Accessed July 2021]

# For send an email code (in separate file - "README_emailcode.txt") base code quoted from: doc.python.org/3/library/email.examples.html [accessed July 2021] code modified to specific needs of this project.
