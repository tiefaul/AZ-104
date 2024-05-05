# AZ-104 Notes

## Azure Application Gateway

- Used by admins to manage requests from clients to their web apps. It listens for incoming traffic to web apps and checks for messages sent via protocols like HTTP.

![Screenshot 2024-04-08 174410.png](./_resources/Screenshot%202024-04-08%20174410.png)

- Clients send requests to your web apps by specifying the IP address or DNS of the application gateway. The gateway then directs the request to a selected web server in your back-end pool according to a set of rules.  
    <br/>

## Things to know about traffic routing

- Azure Application Gateway offers two primary methods for routing traffic
    - **Path-based routing** sends requests with different URL paths to different pools of back-end servers
    - **Multi-site routing** configures more than one web application on the same application gateway instance
- You can configure your application gateway to redirect traffic
- You can implement Application Gateway to rewrite HTTP headers
- Application Gateway allows you to create custom error pages instead of displaying default error pages.  
    <br/>

## Path-based routing

- For **path based routing** think of your web app receiving a requests for video and images. You can use this routing to direct requests for the `/video/\*` path to a back-end pool of servers that are optimized to handle video streaming. and the same for a request for a `/images/\*` path.  
    <br/>

## Multi-site routing

- For this routing consider a config where you need to support traffic to two sites on the same gateway. The application gateway using multi-site routing, gets a request from www.testing.com and another request for www.answers.com and forwards the respected traffic to the back-end pools that support them. NOTE: rules are set on the gateway to route the requests  
    <br/>

## Application Gateway Components

- The components that combine to route requests to a pool of webservers are:
    - **Front-end IP address** - Receives the client requests
    - **Back-end pools** - contain web servers for resources like BMs or VM scale sets. Each pool has a load balancer to distribute the workload across the resources
    - **Routing rules** - define how to analyze the request to direct the request to the correct back-end pool
    - **Health probes** - determine which back-end pool servers are available for load-balancing
    - **Listeners** - receive traffic and route the requests to the back-end pool
    - **Optional Web App Firewall** - checks incoming traffic for common threats before the requests reach the listeners

## How traffic works in Application Firewall

- These are the step:
    - Client request hits the **Front-end IP address**
    - Goes through optional **Firewall**
    - Hits the **listener** (can be multi-site or basic)
        - basic listener only routes request based on the path in the URL
        - Multi-site can also route request by using the hostname element of the URL
        - Listener also handle tls/ssl certificates for securing your application between the user and Application Gateway
    - Listener then routes requests according to the **routing rules**
        - Route rules contain HTTP settings
    - Request goes to **Back-end pools** (collection of web servers)
    - NOTE: **Health probes** are apart of this traffic. They send requests to back-end pools to determine if healthy or not