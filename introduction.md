Z-Ware 
======

Create an applications to control Z-Wave smart home devices like switches, dimmers,
door-locks and sensors.

----

Overview 
---------

Z-Ware is a home control middleware designed for Z-Wave. Z-Ware makes Z-Wave integration
into Smart Home Gateways simple by abstracting the Z-Wave network and devices into simple
to use WebAPI's.

Z-Ware API structure 
-------------------- 
<br>

![zwareAPIStructure](https://raw.githubusercontent.com/IoTWitchCarsten/pictures/master/
zwareAPI_Structure.png) 
<br><br>

**ZWNET**
<br> 
The ZWNET object represents the Z-Wave network. Each Z-Ware application will
only have one ZWNET instant through which network information and functions can be
requested.

The application should start by connecting to the Z-Ware portal using the API's in
[REGISTRATION API](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-95d0-8c2327004894
?workspace=c1e2ac26-947f-42b0-8aaf-5e00544946c8#b48e3252- 691a-49ae-920c-9b176e7ac20e).
Once connected the application may request network information through the API's in
[SYSTEM
API](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-95d0-8c2327004894
?workspace=c1e2ac26-947f-42b0-8aaf-5e00544946c8#934c9681- 898d-4c8c-a685-3af3ade912f9) or
control network functions through the API's in [NETWORK
API](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-95d0-8c2327004894
?workspace=c1e2ac26-947f-42b0-8aaf-5e00544946c8#f6395e1a- 389f-42b4-ab97-67b7163091d0).

The ZWNET object includes a node\_list which is a list of the Z-Wave nodes in the network
represented as ZWNODE objects. The node\_list can be requested using the API
[zwnet_get_node_list](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-
95d0-8c2327004894?workspace=c1e2ac26-947f-42b0-8aaf-
5e00544946c8#dfb6574a-4665-4cb7-b83d-414f8297daf1)

**ZWNODE**
<br> 
Each Z-Wave Node is represented by a ZWNODE object. The application may request node information or control node functions through the API's in [NODE/ENDPOINT API](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-95d0-8c2327004894?workspace=c1e2ac26-947f-42b0-8aaf-5e00544946c8#1a8dddf2-335c-42e7-a6d4-00a1ffa7d86e)

The ZWNODE object includes a ep\_list which is a list of Node Endpoints supported by the node represented as ZWEP objects. The ep\_list can be requested using the API [zwnode_get_ep_list](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-95d0-8c2327004894?workspace=c1e2ac26-947f-42b0-8aaf-5e00544946c8#22e401c9-5db1-487c-8fad-cd73fa4a7873). 


**ZWEP**
<br> 
Each Z-Wave Node Endpoint is represented by a ZWEP object. A Z-Wave node will as minimum have one Endpoint which represents the device. But some Z-Wave nodes may have more Endpoints like a power strip with multiple outlets. For this device each outlet will be displayed as an Endpoint in addition to the device Endpoint. 

The ZWEP object includes a if\_list which is a list of functionality related to the Endpoint represented as ZWIF objects. The if\_list can be requested using the API [zwep_get_if_list](https://z-wareapi.postman.co/collections/5020474-258de107-aed7-432e-95d0-8c2327004894?workspace=c1e2ac26-947f-42b0-8aaf-5e00544946c8#b3e7a2b7-63d1-48f4-a1c3-e827369cc14b)   



**ZWIF**
<br> 
Each functionality/interface in a Z-Wave Node Endpoint is represented by a ZWIF object. The interfaces relates to the Z-Wave Command Classes. So each Command Class supported by the Z-Wave Node Endpoint is represented as a ZWIF object. 



