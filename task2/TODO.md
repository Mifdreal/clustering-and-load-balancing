Запуск:
```bash
cd task2
bash -c 'cd http1/; nohup python3 -m http.server 8888 2>&1 >/dev/null &';
bash -c 'cd http2/; nohup python3 -m http.server 9999 2>&1 >/dev/null &';
bash -c 'cd http3/; nohup python3 -m http.server 7777 2>&1 >/dev/null &';
haproxy -f haproxy.cfg 
```

Проверка
```bash
curl http://127.0.0.1:8088
curl -H "Host: example.local" http://127.0.0.1:8088
for i in `seq 1 40`; do curl -H "Host: example.local" http://127.0.0.1:8088 2>/dev/null; done |sort|uniq -c
```

Завершение работы
```bash
killall python3 haproxy
```
