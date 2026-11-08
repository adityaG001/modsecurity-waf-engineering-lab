# WAF Architecture

## Request flow
1. A client sends an HTTP request to the published WAF listener.
2. ModSecurity processes the request and evaluates enabled CRS rules.
3. The WAF logs or blocks the request according to its engine mode and anomaly thresholds.
4. Allowed requests are reverse-proxied to Juice Shop on the private Docker network.

## Network exposure
- Only the WAF publishes a host port.
- Juice Shop uses `expose` for container-network access and has no host port mapping.
- The supplied Compose file binds the WAF to `127.0.0.1:8080` by default. For access from a separate Kali VM, deliberately change the bind address to the isolated DMZ interface IP and enforce firewall restrictions.
- Never bind the vulnerable application to a public interface.

## Modes
- `DetectionOnly`: inspect and log, but do not block.
- `On`: enforce blocking when the rules and anomaly thresholds indicate a request should be blocked.

Begin in DetectionOnly and establish a benign-traffic baseline before enabling blocking.
