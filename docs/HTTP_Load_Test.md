##HTTP Load test
Using ab that comes with apache
```bash
ab -n 10000 -c 10 http://domain.com
```
`-n` requests => Number of requests to perform

`-c` concurrency => Number of multiple requests to make at a time

`ab -h` for more
