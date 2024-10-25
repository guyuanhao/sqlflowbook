# Installation

Gudu SQLFow is extremely simple to install and is comprised of two parts: frontend and backend. The frontend and backend can be installed on the same server, or they can be installed on two different servers seperately.

* [Linux](linux.md)
* [MacOS](macos.md)
* [Windows](windows.md)

If you need to enable regular job features, you will also need to install Clickhouse on your server: [Clickhouse Installation](clickhouse-installation/clickhouse-for-centos.md).

You can check for [SQLFlow Widget](../../4.-sqlflow-widget/get-started.md) once you have your SQLFlow on-premise Installed on your server and Widget will read the data from the SQLFlow on your server.

### Recommended Configuration

To ensure optimal performance for SQLFlow, we recommend the following configuration:

1. CPU Cores\
   **8 cores** for handling both UI and backend processes efficiently.
2. Memory (RAM) Requirement\
   SQLFlow requires substantial memory; **32GB** RAM is recommended. Customization: Use the `/m` flag to control memory usage as needed. [Learn more about configuring memory.](https://docs.gudusoft.com/1.-introduction/installation/linux#start-backend-services)
3. Storage Requirement\
   At least **500GB** for SQLFlow's storage needs.
