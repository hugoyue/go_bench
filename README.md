# go_bench - a HTTP benchmarking tool

    go_bench is a tiny program that sends some load to a web application.
  
## Installation

```
    go get github.com/linkxzhou/go_bench
```

or

```
    git clone git@github.com:linkxzhou/go_bench.git
    cd go_bench
    go build go_bench.go
```

## Basic Usage

    ./go_bench -n 1000 -c 10 -t 3000 -m GET http://127.0.0.1/hello

    This runs a benchmark for 1000 requests, keeping 10 HTTP connections open, and timeous is 3000ms

    Output:
        Request:
        [1000] http://www.baidu.com
        Summary:
        Total:        5.2124 secs
        Slowest:      0.3283 secs
        Fastest:      0.0195 secs
        Average:      0.0345 secs
        Requests/sec: 191.8491

        Status code distribution:
        [200] 1000 responses

        Latency distribution:
        10% in 0.0253 secs
        25% in 0.0272 secs
        50% in 0.0298 secs
        75% in 0.0350 secs
        90% in 0.0498 secs
        95% in 0.0606 secs
        99% in 0.0872 secs

## Command Line Options

```
    -n  Number of requests to run.
    -c  Number of requests to run concurrently. Total number of requests cannot
        be smaller than the concurency level.
    -q  Rate limit, in seconds (QPS).
    -o  Output type. If none provided, a summary is printed.
        "csv" is the only supported alternative. Dumps the response
        metrics in comma-seperated values format.
    -m  HTTP method, one of GET, POST, PUT, DELETE, HEAD, OPTIONS.
    -H  Custom HTTP header. You can specify as many as needed by repeating the flag.
        for example, -H "Accept: text/html" -H "Content-Type: application/xml" .
    -t  Timeout in ms.
    -A  HTTP Accept header.
    -d  HTTP request body.
    -T  Content-type, defaults to "text/html".
    -a  Basic authentication, username:password.
    -x  HTTP Proxy address as host:port.
    -h2  Make HTTP/2 requests.
    -disable-compression  Disable compression.
    -disable-keepalive    Disable keep-alive, prevents re-use of TCP
                            connections between different HTTP requests.
    -cpus                 Number of used cpu cores.
                            (default for current machine is 4 cores)
    -host                 HTTP Host header.
    -f  Request url file, a launch request in the random selection file
```
You can try : ./go_bench -n 1000 -c 10 -t 3000 -m GET -f urls.txt