# StreamCaster
Fully automated live streaming to multiple platforms.

### Features:

* Fully automated live streaming to multiple platforms.
* Minimal user interaction needed to create, start and stop live streams.
* One single dashboard which allows you to:
  * Monitor your live stream in detail over all platforms
  * Interact with your listeners/viewers over all platforms
* Fully automated VJ to use in your live streams
* Stream title and description are uniform and exactly the same over all platforms
* The logo of your organization is automatically integrated to your live stream
* The DJ name is automatically integrated in your live stream
* Live streams are automatically recorded, without the need for user interaction
* Fully seperate Live- and Test-environments which allows you to test your broadcast setup without bothering your fanbase with test broadcasts

### Applications and design choices:

##### Generic applications:
* [Docker](https://www.docker.com/):
  * Automated deployment of application as a portable, self-sufficient container
* [Alpine linux](https://www.alpinelinux.org/):
  * Designed for security, simplicity, and resource efficiency
* [nginx](https://nginx.org/) with [nginx-rtmp](https://github.com/arut/nginx-rtmp-module):
  * Webserver for streaming to static RTMP endpoints
  * HTTP-JSON statistics
  * Reversed proxy for the Python StreamCaster application
* [STunnel](https://www.stunnel.org/):
  * Used by nginx-rtmp to stream to RTMPS-only endpoints (nginx-rtmp does not offer RTMPS support yet)
* [Icecast](https://icecast.org/):
  * Handles audio-only broadcasts from Traktor e.g.
* [ffmpeg](https://ffmpeg.org/):
  * Custom compiled ffmpeg with support for hardware encoding and several extra codecs (the default Alpine linux ffmpeg package does not support hardware encoding)
* [LiquidSoap](https://www.liquidsoap.info/) (experimental):
  * Can be used to switch from multiple input streams to one output stream without any downtime (TODO figure out if this really works)

##### Python applications and libraries:
* StreamCaster:
  * Custom Python application which:
    * Handles all API requests to/from the supported streaming platforms
    * Offers a statistics API with statistics about this Docker container and all supported streaming platforms
    * Offers a chat API for interacting with users on all supported streaming platforms
* [Uvicorn](https://www.uvicorn.org/):
  * Python webserver for serving API content
* [FastAPI](https://fastapi.tiangolo.com/):
  * A modern, fast (high-performance), web framework for building APIs with Python
* [PyJWT]():
  * Python library which encodes and decodes JSON Web Tokens (OAUTH)
* [SQLAlchemy](https://www.sqlalchemy.org/):
  * Support for SQL databases in Python
* [InstaLiveCLI](https://github.com/RaihanStark/instalivecli):
  * Python script for managing live streams to Instagram
* [TwitchIO](https://github.com/TwitchIO/TwitchIO):
  * Python script for managing live chat with Twitch channels
