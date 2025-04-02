Запуск:
```bash
cd task1
bash -c 'cd http1/; nohup python3 -m http.server 8888 2>&1 >/dev/null &';
bash -c 'cd http2/; nohup python3 -m http.server 9999 2>&1 >/dev/null &';
haproxy -f haproxy.cfg 
```

Проверка
```bash
curl http://127.0.0.1:1325
```

Завершение работы
```bash
killall python3 haproxy
```
