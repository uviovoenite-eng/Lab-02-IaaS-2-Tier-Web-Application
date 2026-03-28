# Lab-02-IaaS-2-Tier-Web-Application

DIAGRAM:

https://lucid.app/lucidchart/85f7c960-c757-45a8-8aa6-1f73290314e7/edit?viewport_loc=-3308%2C-2708%2C3262%2C1900%2C0_0&invitationId=inv_a2c04580-d575-4a16-a8a8-1f8f74e88837


SOP

## Creating a Virtual Network with Public and Private Subnets

### Objective

This SOP outlines the steps to create a virtual network with public and private subnets, deploy virtual machines, and configure network security groups to ensure secure communication between the servers.

### Key Steps

**1. Create Resource Group** [1:03](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=63)

![generated-image-at-00:01:03](https://loom.com/i/26a693d083e345ebb853700d2344242d?workflows_screenshot=true)

- Navigate to the Azure portal.
- Create a new resource group named `Lab 2`.

**2. Create Virtual Network** [2:00](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=120)

![generated-image-at-00:02:00](https://loom.com/i/af224b14ca0147afb60473ef5fa039ad?workflows_screenshot=true)

- In the resource group, create a virtual network.
- Set the region to East Coast.
- Define IP address schemes for public and private subnets.

**3. Create Public Subnet** [3:28](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=208)

![generated-image-at-00:03:28](https://loom.com/i/268903c2af7c4191862c99bab42d19aa?workflows_screenshot=true)

- Create a public subnet named `snetweb`.
- Set the IP range to CIDR notation `/24`.

**4. Create Private Subnet** [4:12](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=252)

![generated-image-at-00:04:12](https://loom.com/i/1a9cdecc4ec2471ba111f87046d12606?workflows_screenshot=true)

- Create a private subnet named `snetdb`.
- Set the starting IP to `.2`.

**5. Deploy Subnets** [5:15](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=315)

![generated-image-at-00:05:15](https://loom.com/i/0d1ce1441d6247eb830d32f45f689583?workflows_screenshot=true)

- Review and create the subnets and virtual network.

**6. Create Web Server VM** [6:13](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=373)

![generated-image-at-00:06:13](https://loom.com/i/aa6ed27b618c47c2ad20acc440b36312?workflows_screenshot=true)

- Navigate to Virtual Machines and click `Create`.
- Name the VM `VM-web-01` and place it in the `Lab 2` resource group.
- Set the region to East Zone and choose Ubuntu as the OS.
- Select the standard size `D4S`.

**7. Configure Web Server VM** [7:16](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=436)

![generated-image-at-00:07:16](https://loom.com/i/3bda91f81b8b4dd08896a19ef3721996?workflows_screenshot=true)

- Generate a key pair named `Key-DashLab02`.
- Allow port 80 for web access.
- Enable Auto Shutdown to save resources.

**8. Create Database Server VM** [9:43](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=583)

![generated-image-at-00:09:43](https://loom.com/i/972ee3db0965480cbc844ab4ca588653?workflows_screenshot=true)

- Create another VM named `VMDB-01` in the same resource group.
- Use the same region, OS, and size as the web server.
- Only allow SSH access (port 22) for security.

**9. Test Connectivity** [13:14](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=794)

![generated-image-at-00:13:14](https://loom.com/i/6620025e28f64d71ad30e7b46fba1cfa?workflows_screenshot=true)

- Use a terminal to ping the database server from the web server to ensure connectivity.

**10. Configure Network Security Groups** [20:04](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=1204)

![generated-image-at-00:20:04](https://loom.com/i/1d6d630ef2d1432c81da6f2c3fd537e2?workflows_screenshot=true)

- Go to the networking settings of the database server.
- Create an inbound rule to allow traffic only from the web server.

**11. Finalize Setup** [23:34](https://loom.com/share/ea1ea8814da342b982e69d70f39481f7?t=1414)

![generated-image-at-00:23:34](https://loom.com/i/0c7e5a46eefe47b98c047717cc430c77?workflows_screenshot=true)

- Ensure that only the web server can access the database server.
- Confirm that all configurations are correct and functioning.

### Cautionary Notes

- Ensure that the resource names are unique to avoid conflicts.
- Be cautious with security group rules to prevent unauthorized access.

### Tips for Efficiency

- Use Terraform for remote deployments to maintain consistency.
- Regularly review and tag resources for better organization.

### Link to Loom

<https://loom.com/share/ea1ea8814da342b982e69d70f39481f7>
