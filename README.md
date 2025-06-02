What TCP Keepalive Tuning Actually Helps With
1. Detecting Dead Connections Sooner
By default, Linux waits 2 hours (tcp_keepalive_time = 7200) before sending a keepalive probe. During that time:

If an upstream device (firewall, SNAT, load balancer) silently drops the idle connection, the app won’t know.

Your app will try to re-use a broken connection — leading to timeouts, hangs, or retries, which look like intermittent latency spikes.

✅ With your new settings:

The node will send probes after 30s of idle

If no response, it retries 3 times (1.5 mins total)

Broken connections are detected and closed faster, preventing app delays
