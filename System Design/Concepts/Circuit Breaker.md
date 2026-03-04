The Circuit Breaker pattern is a resilience pattern used in distributed systems to prevent cascading failures when calling remote services (HTTP, DB, message brokers, etc.).

If a certain amount of requests or actions fail in a given time, block the consumer to prevent overload or misuse. If something is broken, stop using it to protect the system.

### Common Strategies

#### Sliding window
Track request failures over a sliding window of N seconds, if a defined limit was reached, break the circuit.

#### Slow Call Detection
Open breaker if responses are too slow (even if successful).

#### Fallbacks
Instead of returning error:
- Return cached data
- Return default value
- Queue for later processing

### States

The circuit breaker usually has 3 states

1. **Closed** - This is the normal, optimal state. If an opening rule has passed (e.g. 80% of requests to a resource failed), transition to Open.
2. **Open** - Enough requests or operations failed. Send error messages instead of retrying the operation. After a timeout period transition to Half-Open  
3. **Half-Open** - After a timeout allow a small stream of requests to pass, if enough success transition to Closed, otherwise transition to Open.