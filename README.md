# twitch_api_backend_demo
A code test made for "Strafe-Initial-Backend-Test".

# Description

this is a REST API that you can run from your local computer. it let's you connect with a twitch chat
and get some useful information. You can:
- get all the messages sent within a certain period until now
- get the average number of messages within a time period (wether a second, a minute, or an hour).
- get the average number of questions per minute

# Installation

Requirements:
- Python 3.6 or newer
- Flask
- Windows XP/Vista/7/8.1/10 (Why? because it is dependent on os.system to start the tracking processes. In case you know what you are doing, it will be relatively easy to port it to linux-based systems. Without modifications however, you will need to use windows for this.)

Download the folder and extract it to any folder. you should find a file system containing these files and folders

- data
-  chat.db
- error_on_fetching
- bot.py
- server.py
- start.bat

You can start the server in three ways:
* directly click on server.py
* open the command prompt, navigate to your folder and write "py server.py", or
* click on "start.bat"

make sure there aren't any exceptions and that the window does not close.

# Usage

Go to the chrome browser and type:
http://localhost:5000/index
that is a demo page where you don't need to go through the API to directly start the tracking bot.
write the name of a twitch channel and click OK. you will receive a information capsule and a black window will pop up. That window
is the bot fetching messages from the channel and feeding it to the database. You can now use that. Go to
http://localhost:5000/chatlog?secondsBackInTime=60
and you will get a dictionary containing all messages within the last 60 seconds.

to get the average number of messages per minute, we convert it into 60 seconds and go to:
http://localhost:5000/time_avr?seconds=60&channel=<channel>

We also have a mood measurement. We can actually monitor the number of questions per minute. go to
http://localhost:5000/questions_per_minute?channel=<channel>

This is just a fun feature I added for the sake of entertainment, but it may be useful in the future.

# Did something go wrong?

Please make sure that:
- the ClientID and all keys are correct (this is more easily said than done. Believe me. It took me 2 days to figure it out during
  development of this app.)
- the commands given in the os.system calls within the code and in start.bat are compatible with your system. If you try to run
  this from Linux, then you definetly will need to change all the command to fit.
  During my experience, I have stumbled upon many ways to start a python file:
  python server.py
  py server.py
  You have to figure out which one of these are working or not. if none of these commands above work in your command prompt from
  a windows system, you will need to add the python directory to the PATH environment variable and restart the computer.


# Tests
there are a couple of continous test you will need to follow up every now and then:
- in the folder error_on_fetching, all messages that couldn't be added to the database, will be added in this folder as a text file,
with the timestamp as filename, containing the query and the python traceback. You can run this code on many different channels
for weeks straight, and you can then look over all these files and at best fix all problems with just one modification.




Please give me feedback if this code isn't working for you.








