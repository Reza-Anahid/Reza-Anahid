There are 5 OSPF network types:

    Non-Broadcast.
    Broadcast.
    Point-to-Multipoint.
    Point-to-Multipoint Non-Broadcast.
    Point-to-Point.
    
LSA types:

    Type 1 - Represents a router
    Type 2 - Represents the pseudonode (designated router) for a multiaccess link
    Type 3 - A network link summary (internal route)
    Type 4 - Represents an ASBR
    Type 5 - A route external to the OSPF domain
    Type 7 - Used in stub areas in place of a type 5 LS
    
Stub Area:
    
    Backbone area (area 0)
    Standard area
    Stub area
    Totally stubby area
    Not-so-stubby area (NSSA)
    
 
OSPF routers:

    Internal Router
    Backbone Router
    Area Border Router (ABR)
    Autonomous System Boundary Router (ASBR)

   
Links:

    https://packetlife.net/media/blog/attachments/39/ospf_standard_area.jpg
    
    https://packetlife.net/blog/2008/jun/24/ospf-area-types/
    
    https://cisco.tosinso.com/fa/articles/30774/OSPF-%DA%86%DB%8C%D8%B3%D8%AA-%D9%88-%DA%86%DA%AF%D9%88%D9%86%D9%87-%D9%BE%DB%8C%D8%A7%D8%AF%D9%87-%D8%B3%D8%A7%D8%B2%DB%8C-%D9%85%DB%8C-%D8%B4%D9%88%D8%AF%D8%9F
    
    
    
 Building the Adjacency

The adjacency building process takes effect after multiple stages have been fulfilled. Routers that become adjacent will have the exact link-state database. The following is a brief summary of the states an interface passes through before becoming adjacent to another router:

    Down: No information has been received from anybody on the segment.
    Attempt: On non-broadcast multi-access clouds such as Frame Relay and X.25, this state indicates that no recent information has been received from the     neighbor. An effort should be made to contact the neighbor by sending Hello packets at the reduced rate PollInterval.
    Init: The interface has detected a Hello packet coming from a neighbor but bi-directional communication has not yet been established.
    Two-way: There is bi-directional communication with a neighbor. The router has seen itself in the Hello packets coming from a neighbor. At the end of     this stage the DR and BDR election would have been done. At the end of the 2way stage, routers will decide whether to proceed in building an adjacency     or not. The decision is based on whether one of the routers is a DR or BDR or the link is a point-to-point or a virtual link.
    Exstart: Routers are trying to establish the initial sequence number that is going to be used in the information exchange packets. The sequence number     insures that routers always get the most recent information. One router will become the primary and the other will become secondary. The primary      router will poll the secondary for information.
    Exchange: Routers will describe their entire link-state database by sending database description packets. At this state, packets could be flooded to    other interfaces on the router.
    Loading: At this state, routers are finalizing the information exchange. Routers have built a link-state request list and a link-state retransmission     list. Any information that looks incomplete or outdated will be put on the request list. Any update that is sent will be put on the retransmission  list until it gets acknowledged.
    Full: At this state, the adjacency is complete. The neighboring routers are fully adjacent. Adjacent routers will have a similar link-state database.

