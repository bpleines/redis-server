redis-server
=========

An Ansible role to install redis from source

Requirements
------------

Platform Ubuntu

Role Variables
--------------

| Name  | Type | Default Value | Description |
| ------------- | ------------- | ------------- | ------------- |
| redis_bind_address  | String  | 0.0.0.0 | The ip address(es) to accept remote redis connections from |
| redis_install_dir | String | /var/lib/redis | The directory to install redis to and from. Also the home directory for the redis unix user |
| redis_server_port | int | 6379 | The port which redis accepts incoming connections from |
| redis_user | String | redis | The unix user to run the redis-server service as |
| redis_version | String | 5.0.7 | The version of redis to install. At the time of writing 5.0.7 is the latest stable version. Can also be supplied as "stable" |
| redis_config_file_path | String | /etc/redis/redis.conf | The filepath for the redis configuration file |
| redis_log_file_path | String | /var/log/redis/redis.log | The filepath for the redis log file |
| redis_maxmemory_percent | int | 80 | The percent of total server memory to allocate to redis cache. Explicitly setting this value avoids the redis server from OOM crashing and instead provides errors early when this memory threshold is reached |
| redis_replication_backlog_size_percent | int | The percent of total server memory to allocate to the replication backlog. A larger replication backlog reduces potential for full synchronizations which can negatively affect performance |
| redis_tcp_backlog | String | 511 | The size of the complete connection queue. Currently this size dictates the redis_tcp_backlog setting AND the unix somaxconn value |

Dependencies
------------

N/A

Example Playbooks
----------------

    - name: Install a redis server from source
      hosts: redis-server 
      roles:
        - role: redis-server
