# Day 2 — Load Baseline Test

## 1. Objective

The objective of this exercise is to understand how JMeter generates load using virtual users and how application performance metrics change as the number of virtual users increases.

The test uses the Restful Booker `/ping` API as a simple endpoint so that the focus remains on understanding:

- Virtual users / threads
- Ramp-up period
- Loop count
- Request execution
- Response time
- Throughput
- Error percentage
- Basic load comparison

This is a learning baseline, not a production capacity test.

---

## 2. Key Terms

| Term | Meaning |
|---|---|
| **Virtual User / Thread** | A simulated user executing the configured JMeter scenario |
| **Thread Group** | Controls the number of users, ramp-up period and iterations |
| **Ramp-up** | The time over which JMeter starts the configured users |
| **Loop Count** | Number of times each virtual user executes the scenario |
| **Response Time** | Time measured for the request/response interaction |
| **Throughput** | Rate at which requests are completed over a period of time |
| **Error %** | Percentage of requests recorded as failures |

---

## 3. Test Scenario

The same API request was executed with different numbers of virtual users.

```text
Virtual Users
      ↓
GET /ping
      ↓
Restful Booker API
      ↓
Response
      ↓
JMeter Metrics

---

## 4. Test Configuration

The same `GET /ping` request was executed with different virtual-user loads.

| Users | Ramp-up | Loop Count | Total Requests |
|---:|---:|---:|---:|
| 1 | 1 sec | 10 | 10 |
| 10 | 10 sec | 10 | 100 |
| 25 | 25 sec | 10 | 250 |

### JMeter Configuration

- **Test Plan:** Restful Booker - Performance Testing
- **Thread Group:** Used to control virtual users
- **HTTP Request:** `GET /ping`
- **Loop Count:** 10
- **Listener:** View Results Tree used during learning
- **Environment:** Local JMeter execution against Restful Booker
- **Purpose:** Baseline performance learning

---

## 5. Test Results

The following results were observed during the load baseline tests.

| Users | Ramp-up | Loops | Requests | Avg Response Time (ms) | Throughput (requests/sec) | Error % |
|------:|--------:|------:|---------:|-----------------------:|--------------------------:|--------:|
| 1 | 1 sec | 10 | 10 | 319 | 3.1 | 0% |
| 10 | 10 sec | 10 | 100 | 303 | 8.3 | 0% |
| 25 | 25 sec | 10 | 250 | 309 | 9.2 | 0% |

---

## 6. Understanding the Results

### 6.1 Response Time

The average response time remained relatively stable:

- 1 user → **319 ms**
- 10 users → **303 ms**
- 25 users → **309 ms**

There was no significant increase in average response time as the number of users increased from 1 to 25 during this short test.

This indicates that the API continued responding within a similar response-time range under this particular workload.

However, this result should not be interpreted as proof that the system can support unlimited users.

---

### 6.2 Throughput

Throughput increased as the number of virtual users increased:

- 1 user → **3.1 requests/sec**
- 10 users → **8.3 requests/sec**
- 25 users → **9.2 requests/sec**

The increase was not linear.

For example, increasing users from 10 to 25 did not produce a proportional increase in throughput.

This can happen because throughput depends on several factors, including:

- Response time
- Server processing capacity
- Network latency
- Client/JMeter limitations
- Concurrent request handling
- Application architecture

---

### 6.3 Error Percentage

All three tests recorded:

**Error % = 0%**

This means JMeter did not record failed requests during these executions.

However, zero errors in a short baseline test does not prove that the application will remain error-free under much higher or longer loads.

---

## 7. What Did We Learn?

From this exercise, the following JMeter concepts were understood:

1. A JMeter **Thread represents a virtual user**.
2. The **Thread Group** controls the number of virtual users.
3. **Ramp-up** controls how quickly users are started.
4. **Loop Count** controls how many times each user executes the scenario.
5. Increasing users increases the amount of concurrent load placed on the application.
6. **Response time** shows how long requests take to complete.
7. **Throughput** shows how many requests are processed over time.
8. **Error %** shows the percentage of failed requests.
9. Performance results must be compared across different workloads rather than looking at a single test.
10. A short test result should not be treated as the maximum capacity of an application.

---

## 8. Important Learning — Why 9.2 Requests/sec Is NOT the System Limit

The 25-user test produced approximately:

**9.2 requests/sec**

This does **not** mean that the Restful Booker API can support a maximum of 9.2 requests/sec.

This test was designed as a learning baseline and had:

- A small number of users
- Only 10 iterations per user
- A short execution duration
- No server CPU monitoring
- No memory monitoring
- No database monitoring
- No infrastructure monitoring

To determine system capacity, a more controlled performance test would be required with increasing load, longer execution duration, repeated runs, and server-side monitoring.

Therefore:

> **9.2 requests/sec is an observed throughput for this specific test configuration, not the application's maximum capacity.**

---

## 9. Day 2 Conclusion

Day 2 demonstrated how JMeter generates increasing load using virtual users and how basic performance metrics change as the load increases.

The baseline results showed:

- **0% errors** for all tested loads
- Average response time remained around **300–320 ms**
- Throughput increased from **3.1 to 9.2 requests/sec**
- Throughput did not increase linearly with the number of users

The main objective of this exercise was not to find the application's maximum capacity, but to understand how JMeter users, ramp-up, loops, response time, throughput and errors relate to each other.

---

## 10. Next Step — Day 3

Day 3 will move from the simple `/ping` endpoint to a more realistic API workload.

The scenario will use the Restful Booker APIs to model a business workflow such as:

```text
Authenticate
     ↓
Get Booking
     ↓
Create Booking
     ↓
Update Booking
     ↓
Get Booking