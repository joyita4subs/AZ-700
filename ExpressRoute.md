
Quick mental model
CloudExchange → “I’m in the same building, just connect me”
Point-to-Point → “Give me a private line”
Any-to-Any (IPVPN) → “Add Microsoft to my existing WAN”
ExpressRoute Direct → “I’ll connect straight to Microsoft myself”


Start
 |
 |-- Do you need very high bandwidth (10/100 Gbps) and direct control?
 |        |-- YES → ExpressRoute Direct
 |        |-- NO →
 |
 |-- Are you already in a colocation facility with a cloud exchange (e.g., Equinix)?
 |        |-- YES → CloudExchange Colocation
 |        |-- NO →
 |
 |-- Do you already have an MPLS/IPVPN network connecting multiple sites?
 |        |-- YES → Any-to-Any (IPVPN)
 |        |-- NO →
 |
 |-- Do you want a dedicated private connection from your site to Microsoft?
          |-- YES → Point-to-Point Ethernet