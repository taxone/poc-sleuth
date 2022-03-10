# poc-sleuth

Try:

```
curl --request GET --url http://localhost:8081/apigw/get 
```

and this is the log:

```
2022-03-10 09:20:40.220[0;39m [32mDEBUG [sleuth-poc,e6b60512cdeacd74,e6b60512cdeacd74][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mo.s.c.g.h.RoutePredicateHandlerMapping  [0;39m [2m:[0;39m Route matched: myrule
[2m2022-03-10 09:20:40.220[0;39m [32mDEBUG [sleuth-poc,e6b60512cdeacd74,e6b60512cdeacd74][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mo.s.c.g.h.RoutePredicateHandlerMapping  [0;39m [2m:[0;39m Mapping [Exchange: GET http://localhost:8081/apigw/get] to Route{id='myrule', uri=https://httpbin.org:443, order=0, predicate=Paths: [/apigw/get/**], match trailing slash: true, gatewayFilters=[[[RewritePath /apigw(?<segment>/?.*) = '${segment}'], order = 1]], metadata={}}
[2m2022-03-10 09:20:40.220[0;39m [32mDEBUG [sleuth-poc,e6b60512cdeacd74,e6b60512cdeacd74][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mo.s.c.g.h.RoutePredicateHandlerMapping  [0;39m [2m:[0;39m [116abe06-3] Mapped to org.springframework.cloud.gateway.handler.FilteringWebHandler@67dceb32
[2m2022-03-10 09:20:40.221[0;39m [32mDEBUG [sleuth-poc,e6b60512cdeacd74,e6b60512cdeacd74][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mo.s.c.g.handler.FilteringWebHandler     [0;39m [2m:[0;39m Sorted gatewayFilterFactories: [[GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.RemoveCachedBodyFilter@26c89563}, order = -2147483648], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.AdaptCachedBodyGlobalFilter@358ab600}, order = -2147482648], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.NettyWriteResponseFilter@2a8a4e0c}, order = -1], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.ForwardPathFilter@20f6f88c}, order = 0], [[RewritePath /apigw(?<segment>/?.*) = '${segment}'], order = 1], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.RouteToRequestUrlFilter@3bd6ba24}, order = 10000], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.config.GatewayNoLoadBalancerClientAutoConfiguration$NoLoadBalancerClientFilter@4c7e978c}, order = 10150], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.WebsocketRoutingFilter@4277127c}, order = 2147483646], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.NettyRoutingFilter@20d87335}, order = 2147483647], [GatewayFilterAdapter{delegate=org.springframework.cloud.gateway.filter.ForwardRoutingFilter@58f437b0}, order = 2147483647]]
[2m2022-03-10 09:20:40.769[0;39m [32mDEBUG [sleuth-poc,,][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mr.netty.http.client.HttpClientConnect   [0;39m [2m:[0;39m [a16ba65b-1, L:/192.168.1.109:59032 - R:httpbin.org/54.221.78.73:443] Handler is being applied: {uri=https://httpbin.org/get, method=GET}
[2m2022-03-10 09:20:40.890[0;39m [32mDEBUG [sleuth-poc,,][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mr.n.http.client.HttpClientOperations    [0;39m [2m:[0;39m [a16ba65b-1, L:/192.168.1.109:59032 - R:httpbin.org/54.221.78.73:443] Received response (auto-read:false) : [Date=Thu, 10 Mar 2022 08:20:40 GMT, Content-Type=application/json, Connection=keep-alive, Server=gunicorn/19.9.0, Access-Control-Allow-Origin=*, Access-Control-Allow-Credentials=true, content-length=623]
[2m2022-03-10 09:20:40.891[0;39m [32mDEBUG [sleuth-poc,,][0;39m [35m19360[0;39m [2m---[0;39m [2m[ctor-http-nio-4][0;39m [36mr.n.http.client.HttpClientOperations    [0;39m [2m:[0;39m [a16ba65b-1, L:/192.168.1.109:59032 - R:httpbin.org/54.221.78.73:443] Received last HTTP packet
```

The request logs have spanId and TraceId, but response logs have not.
