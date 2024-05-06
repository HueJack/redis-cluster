## First start
```docker compose up redis_cluster```

## If you stopped cluster then start cluster without redis_cluster service
```docker compose up redis_1 redis_2 redis_3 redis_4 redis_5 redis_6```

## Restore redis cluster data from backup
1. Stop the cluster
2. In the config of one of the nodes set the value ``appendonly no``.
3. Copy the backup to the /data folder of the node
4. Run only this node
5. When the startup process is over, open the container, connect to redis-cli and enter the ```bgrewriteaof`` command.
6. Then you can enter the command ```info``` and check the status ```aof_rewrite_in_progress```.
7. When the process completes and the status is 0, the node should be stopped and the status returned ``appendonly yes``.
8. Start the node again and only it started then start the remaining nodes in the cluster 

Good luck.
