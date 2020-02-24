What advantages does the NLB have over the Application Load Balancer (ALB)?

A Network Load Balancer is capable of handling millions of requests per second while maintaining ultra-low latencies, making it ideal for load balancing TCP traffic. NLB is optimized to handle sudden and volatile traffic patterns while using a single static IP address per Availability Zone. The benefits of using a NLB are:

## Static IP/elastic IP addresses:  ``For each Availability Zone (AZ) you enable on the NLB, you have a network interface. Each load balancer node in the AZ uses this network interface to get a static IP address. You can also use Elastic IP to assign a fixed IP address for each Availability Zone.``

Scalability: Ability to handle volatile workloads and scale to millions of requests per second.
Zonal isolation: The Network Load Balancer can be used for application architectures within a Single Zone. Network Load Balancers attempt to route a series of requests from a particular source to targets in a single AZ while still providing automatic failover should those targets become unavailable.
Source/remote address preservation: With a Network Load Balancer, the original source IP address and source ports for the incoming connections remain unmodified. With Classic and Application load balancers, we had to use HTTP header X-Forwarded-For to get the remote IP address.
Long-lived TCP connections: Network Load Balancer supports long-running TCP connections that can be open for months or years, making it ideal for WebSocket-type applications, IoT, gaming, and messaging applications.
Reduced bandwidth usage: Most applications are bandwidth-bound and should see a cost reduction (for load balancing) of about 25% compared to Application or Classic Load Balancers.
SSL termination: SSL termination will need to happen at the backend, since SSL termination on NLB for Kubernetes is not yet available.``

For any NLB usage, the backend security groups control the access to the application (NLB does not have security groups of it own). The worker node security group handles the security for inbound/ outbound traffic.
