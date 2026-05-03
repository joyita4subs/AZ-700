
# Express Route

## Select an ExpressRoute connectivity model
- CloudExchange → “I’m in the same building, just connect me”
- Point-to-Point → “Give me a private line”
- Any-to-Any (IPVPN) → “Add Microsoft to my existing WAN”
- ExpressRoute Direct → “I’ll connect straight to Microsoft myself”

###  CloudExchange Colocation

What it is:
You place your equipment in the same data center as a Microsoft-approved connectivity provider (like Equinix).

How it works:

Your network sits in a colocation facility
A provider in that facility already has a connection to Microsoft
You just cross-connect (a short cable) to that provider

Plain English analogy:
You and provider are in the same building, and you plug a cable into a neighbor who already has a direct line to Microsoft.

When it’s used:

You already use colocation facilities
You want fast setup with minimal infrastructure changes

### Point-to-Point Ethernet Connection

What it is:
A dedicated private line from your location directly to Microsoft.

How it works:

A telecom provider gives you a private circuit
That circuit goes straight from your datacenter to Microsoft’s edge

Plain English analogy:
A private highway built just for you between your office and Microsoft—no sharing with others.

When it’s used:

You want predictable performance and isolation
You have a single or few locations needing connectivity

### Any-to-Any (IPVPN) Connection

What it is:
You connect through a provider’s MPLS/IPVPN network that links multiple sites together.

How it works:

Your sites are already connected via an MPLS network
The provider extends that network to Microsoft
Microsoft becomes just another “site” in your WAN

Plain English analogy:
Microsoft becomes another branch office on your company network.

When it’s used:

You have multiple offices already on MPLS
You want seamless integration without building separate links

### ExpressRoute Direct

What it is:
You connect directly to Microsoft routers at an ExpressRoute location using very high bandwidth ports.

How it works:

You bypass providers for the actual connection
You plug directly into Microsoft’s edge routers
You get dedicated ports (10 Gbps or 100 Gbps)

Plain English analogy:
Instead of going through a service provider, you plug straight into Microsoft’s network backbone.

When it’s used:

Very high bandwidth needs (massive data transfer)
Strict compliance or isolation requirements
You want full control over connectivity

```md
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
          |-- YES → Point-to-Point Ethernet managed by provider
```

### Important Info

#### The distinction between Point-to-Point vs ExpressRoute Direct

Point-to-Point (“Give me a private line”)
You get a dedicated circuit, but it’s delivered and managed by a provider. That provider owns the path between you and Microsoft.

ExpressRoute Direct (“I’ll connect straight to Microsoft myself”)
You bypass providers for the circuit itself and plug directly into Microsoft’s edge routers at a peering location—you control the connection and capacity (10/100 Gbps ports).

## Select an appropriate ExpressRoute SKU and tier
    
### SKU Tiers

- Local: Provides access only to Azure services within the same region as the peering location.
- Standard: Provides access to all Azure services in all regions within the same geopolitical area (e.g., US East to US West).
- Premium: Provides access to all Azure services globally, allowing you to connect to any region worldwide

### SKU family
- MeteredData: You pay a monthly fee, and all inbound data transfer is free, with a per-GB charge for outbound data.
- UnlimitedData: You pay a higher flat monthly fee, with no additional charges for data transfer.

![alt text](ExpressRoute\SKU.png)

### Gateway SKUs
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-about-virtual-network-gateways>


## Design and implement ExpressRoute to meet requirements, including cross-region connectivity, redundancy, and disaster recovery
- <https://learn.microsoft.com/en-us/azure/expressroute/designing-for-disaster-recovery-with-expressroute-privatepeering#large-distributed-enterprise-network>


## Design and implement ExpressRoute Global Reach, FastPath and ExpressRoute Direct

<https://learn.microsoft.com/en-us/azure/well-architected/service-guides/azure-expressroute?toc=/azure/expressroute/toc.json>


### Global Reach
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-global-reach>
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-set-global-reach-portal#expressroute-circuits-in-the-same-azure-subscription>

![alt text](https://learn.microsoft.com/en-us/azure/expressroute/media/expressroute-global-reach/global-reach-infrastructure.png)

### FastPath
- <https://learn.microsoft.com/en-us/azure/expressroute/about-fastpath>
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-linkvnet-portal-resource-manager#configure-expressroute-fastpath>

![alt text](https://learn.microsoft.com/en-us/azure/expressroute/media/about-fastpath/fastpath-vnet-peering.png)

### ExpressRoute Direct
ExpressRoute Direct gives you the ability to connect directly into the Microsoft global network at peering locations strategically distributed around the world. ExpressRoute Direct provides dual 400-Gbps, 100-Gbps or 10-Gbps connectivity that supports active-active connectivity at scale. You can work with any service provider to set up ExpressRoute Direct.
<https://learn.microsoft.com/en-us/azure/expressroute/expressroute-erdirect-about>

## Choose between Azure private peering only, Microsoft peering only, or both
- https://learn.microsoft.com/en-us/azure/expressroute/expressroute-circuit-peerings#routingdomains

![alt text](https://learn.microsoft.com/en-us/azure/expressroute/media/expressroute-circuit-peerings/expressroute-peerings.png)

## Configure Microsoft peering
- [MSFT Peering](<https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-routing-portal-resource-manager#to-create-microsoft-peering>)

## Configure Azure private peering
- [Azure Private Peering](<https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-routing-portal-resource-manager#to-create-azure-private-peering>)

## Create and configure an ExpressRoute circuit
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-circuit-portal-resource-manager>

## Create and configure an ExpressRoute gateway
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-add-gateway-portal-resource-manager>

## Configure encryption over ExpressRoute
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-about-encryption>

## Implement Bidirectional Forwarding Detection
- <https://learn.microsoft.com/en-us/azure/expressroute/expressroute-bfd>

## Diagnose and resolve ExpressRoute connection issues