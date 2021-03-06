# Make a streaming Twitter sentiment analysis system
## Laboratory 1 requirements

- You will have to read 2 SSE streams of actual Twitter API tweets in JSON format.
- For Elixir use this project to read SSE: https://github.com/cwc/eventsource_ex
- The streams are available from a Docker container, alexburlacu/rtp-server:faf18x on port 4000 The rate of messages varies by up to an order of magnitude, from 100s to 1000s.
- Then, you route the messages to a group of workers that need to be autoscaled, you will need to scale up the workers (have more) when the rate is high, and less actors when the rate is low
- Route/load balance messages among worker actors in a round robin fashion
- Occasionally you will receive "kill messages", on which you have to crash the workers.
- To continue running the system you will have to have a supervisor/restart policy for the workers.
- The worker actors also must have a random sleep, in the range of 50ms to 500ms, normally distributed. This is necessary to make the system behave more like a real one + give the router/load balancer a bit of a hard time + for the optional speculative execution. The output will be shown as log messages.

## Setup
- install : mix deps.get
- build   : mix escript.build
- environment variables:
   - TWITTER_CONSUMER_KEY
   - TWITTER_CONSUMER_SECRET
   - TWITTER_ACCESS_TOKEN
   - TWITTER_ACCESS_TOKEN_SECRET
   




