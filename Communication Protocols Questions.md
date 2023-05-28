# Communication protocols interview questions #

## Questions ##
* [Q1: What is the difference between synchronous and asynchronous communication protocols?](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Communication%20Protocols.md#q1-what-is-the-difference-between-synchronous-and-asynchronous-communication-protocols)


## Questions & Answers ##

### Q1: What is the difference between synchronous and asynchronous communication protocols? ###

| Synchronous | Asynchronous|
| ----------- | ----------- |
| Data is transmitted in a continuous stream, and both the sender and receiver must be synchronized.| Data is transmitted in individual packets or characters, without a continuous stream or fixed timing.|
| Timing is critical, as data is transmitted in fixed intervals or with a clock signal.| More flexible and tolerant to timing variations, as the receiver can synchronize to each packet independently.|
|The sender and receiver operate on a shared clock or use predefined timing signals to ensure proper data transmission. |The sender and receiver do not need to share a clock signal, making asynchronous communication simpler and more versatile. |
| Typically faster and more reliable, but it requires more precise timing and additional hardware for synchronization. |Commonly used for slower data rates and when precise timing is not critical. |
