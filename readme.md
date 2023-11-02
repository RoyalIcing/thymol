# Thymol

## Deployed to AWS Lambda via [Cargo Lambda](https://www.cargo-lambda.info)

- us-east-1: https://qz4t52v34f7nbojf5pbuspbpka0gihlj.lambda-url.us-east-1.on.aws/
- ap-southeast-2: https://qdnxkqgk4agipwznzh3zd5ueke0hmjzm.lambda-url.ap-southeast-2.on.aws/

### Latency:

Loaded from Tasmania in southern Australia.

~~~
$ httpstat "https://qz4t52v34f7nbojf5pbuspbpka0gihlj.lambda-url.us-east-1.on.aws/"
Connected to 52.45.100.6:443

HTTP/1.1 200 OK
Date: Thu, 02 Nov 2023 01:07:18 GMT
Content-Type: text/html
Content-Length: 47
Connection: keep-alive
x-amzn-RequestId: cc3301a1-31e3-4b42-bdad-02cfb352cceb
X-Amzn-Trace-Id: root=1-6542f645-47013b1c100b7cf77408a2c8;sampled=0;lineage=ce35967e:0

  DNS Lookup   TCP Connection   TLS Handshake   Server Processing   Content Transfer
[    68ms    |      283ms     |     655ms     |      1017ms       |        1ms       ]
             |                |               |                   |                  |
    namelookup:68ms           |               |                   |                  |
                        connect:351ms         |                   |                  |
                                    pretransfer:1006ms            |                  |
                                                      starttransfer:2023ms           |
                                                                                 total:2024ms 

$ httpstat "https://qdnxkqgk4agipwznzh3zd5ueke0hmjzm.lambda-url.ap-southeast-2.on.aws/"
Connected to 13.237.69.204:443

HTTP/1.1 200 OK
Date: Thu, 02 Nov 2023 01:11:31 GMT
Content-Type: text/html
Content-Length: 47
Connection: keep-alive
x-amzn-RequestId: 2208f9d0-ebd7-4082-862c-dd685f3f8448
X-Amzn-Trace-Id: root=1-6542f742-06eb32bb4a5976cf601d16e4;sampled=0;lineage=86204974:0

  DNS Lookup   TCP Connection   TLS Handshake   Server Processing   Content Transfer
[    350ms   |      47ms      |     142ms     |       802ms       |        0ms       ]
             |                |               |                   |                  |
    namelookup:350ms          |               |                   |                  |
                        connect:397ms         |                   |                  |
                                    pretransfer:539ms             |                  |
                                                      starttransfer:1341ms           |
                                                                                 total:1341ms 
~~~