# V2ray Setup

## install on debian/ubuntu servers

1. install required packages by `sudo apt install -y unzip wget socat`

2. download v2ray core with `wget https://github.com/v2ray/v2ray-core/releases/download/v4.28.2/v2ray-linux-64.zip -O v2ray-linux-64.zip`
> or download latest v2ray core for linux from `https://github.com/v2ray/v2ray-core/releases`

3. unzip `unzip v2ray-linux-64.zip  -d v2ray`

4. set `server-config.json` file on `v2ray/` folder as `config.json` file

5. run bellow script (as `run.sh` file):
```
killall -9 v2ray
killall -9 socat

nohup ./v2ray -config=config.json &

nohup /usr/bin/socat TCP4-LISTEN:2084,reuseaddr,fork TCP4:127.0.0.1:2083 &
nohup /usr/bin/socat TCP4-LISTEN:8081,reuseaddr,fork TCP4:127.0.0.1:8080 &
```

## connect to v2ray client

### via terminal (linux, mac)

1. download v2ray core
2. set `client-config.json` file on `v2ray/` folder as `config.json` file
3. change v2ray server ip address
4. run `./v2ray -config=config.json`
5. now you have bellow proxies:
    - socks5: 127.0.0.1:10808
    - http: 127.0.0.1:10809

## generate vmess link

1. clone project on `v2ray/` via `git clone https://github.com/boypt/vmess2json`
2. run `./vmess2json/json2vmess.py fake-server-config.json --addr <your-ip>`
3. output is like:
```
vmess://eyJhZGQiOiAiMjAwMToxOWYwOmIwMDI6M2QwOjU0MDA6NGZmOmZlM2Q6OTY5MSIsICJhaWQiOiAiNjQiLCAiaG9zdCI6ICIiLC
AiaWQiOiAiNWE5OTNmNjEtNzY4NC00YWMxLWIyMmMtNDhlZjkzNDNiNzMxIiwgIm5ldCI6ICJ0Y3AiLCAicGF0aCI6ICIiLCAicG9ydCI6
ICI4MDgwIiwgInBzIjogIjIwMDE6MTlmMDpiMDAyOjNkMDo1NDAwOjRmZjpmZTNkOjk2OTEvdGNwIiwgInRscyI6ICIiLCAidHlwZSI6IC
JodHRwIiwgInYiOiAiMiJ9

vmess://eyJhZGQiOiAiMjAwMToxOWYwOmIwMDI6M2QwOjU0MDA6NGZmOmZlM2Q6OTY5MSIsICJhaWQiOiAiMCIsICJob3N0IjogIiIsIC
JpZCI6ICI1YTk5M2Y2MS03Njg0LTRhYzEtYjIyYy00OGVmOTM0M2I3MzEiLCAibmV0IjogIndzIiwgInBhdGgiOiAiIiwgInBvcnQiOiAi
MjA4MyIsICJwcyI6ICIyMDAxOjE5ZjA6YjAwMjozZDA6NTQwMDo0ZmY6ZmUzZDo5NjkxL3dzIiwgInRscyI6ICIiLCAidHlwZSI6ICJub2
5lIiwgInYiOiAiMiJ9
```