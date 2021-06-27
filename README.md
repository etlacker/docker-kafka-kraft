# Docker Kafka Kraft

Apache Kafka Docker image using using Kafka Raft metadata mode (KRaft). In KRaft the Kafka metadata information will be stored as a partition within Kafka itself. There will be a KRaft Quorum of controller nodes which will be used to store the metadata. The metadata will be stored in an internal Kafka topic `@metadata`.

**IMPORTANT: THIS IMAGE IS ONLY VALID FOR TEST PURPOSES AND NOT PRODUCTION USE.**

## Getting Started

```bash
  $ docker pull moeenz/docker-kafka-kraft
  $ docker run -e CONTAINER_HOST_NAME=kafka -e CREATE_TOPICS=topic-a,topic-b,topic-c moeenz/docker-kafka-kraft
```

- Now you can reach the container at `localhost:9093` on your host machine or inside Docker network with hostname `kafka`.
- Comma seperated values received by `CREATE_TOPICS` env will be used to create topics at startup time.

### Compose Example

```yaml
version: "3.8"

services:
  kafka:
    image: moeenz/docker-kafka-kraft:latest
    restart: always
    ports:
      - "9093:9093"
    environment:
      - CONTAINER_HOST_NAME=kafka
```

## Environment Variables

| Name                      | Type     | Description                                                    | Example                 |
| ------------------------- | -------- | -------------------------------------------------------------- | ----------------------- |
| KRAFT_CONTAINER_HOST_NAME | string   | Hostname for the running container as the Kafka listener       | kafka                   |
| KRAFT_CREATE_TOPICS       | []string | Comma separated list of topics to be created post server setup | topic-a,topic-b,topic-c |

## Resources

- [https://adityasridhar.com/posts/how-to-easily-install-kafka-without-zookeeper](https://adityasridhar.com/posts/how-to-easily-install-kafka-without-zookeeper)

## License

MIT License

Copyright (c) 2021 docker-kafka-kraft

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
