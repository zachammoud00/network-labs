# Enable Password vs Enable Secret 

## Objective 
Compare the behavior and security differences between 'enable password' and 'enable secret' on Cisco IOS devices. 

## Topology
Single Cisco switch configured in Packet Tracer

## Configuration 
enable 
configure terminal
enable password cisco-switch
enable secret cisco
end

## Verification 
show running-config

## Output 
enable secret 5 $1$mERr$PyIQfEZgC9xIpNiGymPTe/

enable password cisco

## Conclusion
When viewing the running configuration file the password appears as plain text in the configuration file in comparison to the secret which is encrypted.

When both secret and password are enabled, the Cisco IOS will give secret precedence in protecting the privileged EXEC mode. 

enable secret should always be used over enable password to protect privileged EXEC mode on a Cisco IOS device. 



