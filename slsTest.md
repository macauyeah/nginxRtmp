# docker command
## start server command
```
docker run -d -p 8080:8080/udp --name sls rtainjapan/srt-live-server:master
```

## stop and remove server command
```
docker stop sls
docker rm sls
```

# obs upload
```
srt://[your.sls.ip]:8080?streamid=uplive.sls.com/live/test

srt://127.0.0.1:8080?streamid=uplive.sls.com/live/test
```

# obs media source
```
srt://[your.sls.ip]:8080?streamid=live.sls.com/live/test

srt://127.0.0.1:8080?streamid=live.sls.com/live/test
```


ffplay -fflags nobuffer -i "srt://[127.0.0.1:8080?streamid=live.sls.com/live/test"