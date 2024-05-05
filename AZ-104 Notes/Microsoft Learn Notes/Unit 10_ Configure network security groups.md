# AZ-104 Notes

## Things to know about network security groups

- A network security group can be associated to a subnet or a network interface
- A network security group can be associated multiple times  
    <br/>

## Things to know about security rules

- Azure creates default security rules within the network security group, some examples are:
    - `DenyAllInbound` traffic
    - `AllowInternetOutbound` traffic
- Each rule is assigned a priority value. When a rule has a low priority value, the rule has a higher priority in terms of order processing
- You cannot remove the default security rules
- You can override a default security rule by creating another security rule that has a higher priority setting  
    <br/>

## Determine network security group effective rules

- Azure processes the conditions in each rule defined for each virtual machine in your configuration
    - Inbound Traffic: Azure processes the network security group security rules for any associated subnets and then any associated network interfaces
    - Outbound Traffic: Azure reverses this, checks for network security group security rules for any associated network interfaces and then the associated subnets
    - For both inbound and outbound evaluation process, Azure also check how to apply the rules for intra-subnet traffic  
        <br/><br/>![Screenshot 2024-04-02 175124.png](./_resources/Screenshot%202024-04-02%20175124.png)  
        <br/><br/>![Screenshot 2024-04-02 175145.png](./_resources/Screenshot%202024-04-02%20175145.png)  
        <br/>

## Application Security Groups

- This enables you to group VMs based on the applications they run, their function, or their role within the network
- Once you have created the Application security group, you can then create the network security rules that reference the ASG rather than individual VMs.