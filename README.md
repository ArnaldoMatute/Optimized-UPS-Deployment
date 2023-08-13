## UPS Deploy - Costs Optimization with Gurobi

Deploying a UPS could be an expensive task considering how heavy and big its components are. Battery cabinets could weigh tons and PDUs (Power Distribution Units) are also critical and costly. Space constraints are also pitfalls we can find often when there are other pieces of equipment in the same room. Then, sometimes PDUs o battery cabinets must be installed far away from the UPS, involving crazy long cables, which causes to deal with considerable costs and voltage drops. In this example, we have a typical case where the UPS has been installed, but there are just eight available spots for battery cabinets and PDUs.

![UPSDeployGurobi3](https://github.com/ArnaldoMatute/Optimized-UPS-Deployment/assets/63328827/c5e1b0cb-1959-4b4d-a509-f377740a9861)


For each spot, the installation costs have been calculated. They rely on the fact that, for instance, spot 4 is already free to use for any type of cabinet (Battery or PDU). On the other hand, spots 2 and 3 have other equipment to be retired, which elevates their costs. Spot 5 is also easy for installing cabinets, but it is outside the room and needs long cables to connect what it will have. Enumerating all the details about the cost of installing something at each spot can be a never-ending story. The following table summarizes the costs and the length of the cables needed for each spot.

## Cable lengths and Deploying costs to each spot 

|  Spot |  Length [m] |  Cost for Battery [\$] |  Cost for PDU [\$] |  MaxPDURate [kVA] |
| --- | --- | --- | --- | --- |
|  1 |   6 |   1000 |  500 |  30 |
|  2 |  10 |  700 |  350 |  40 |
|  3 |  12 |  800 |  550 |  80 |
|  4 |  15 |  400 |  100 |  60 |
|  5 |  20 |  650 |  250 |  20 |
|  6 |  6 |  750 |  400 |  50 |
|  7 |  8 |  950 |  950 |  20 |
|  8 |  8 |  950 |  950 |  20 |

Due to further situations found when defining the cable routing and sizing, which could be physical or even of availability or budgetary, other limitations showed up. It has not been always feasible to deploy thick cables between the UPS and each PDU. This limits the power that could flow. This constraint has been found concerning just for PDU and not for Batteries. The last column in the prior table shows the maximum rate in kVA that could possibly flow to each spot.

Additionally, there were other issues to pay attention to:

- Spots 7 and 8 are not suitable for battery cabinets due to constraints in the floor construction.
- At least, four PDUs must be deployed.
- Just two battery banks will be installed
- The must be enough number of PDUs to fully load the Ups (240kVA)

Finally, the costs of each meter of cable are:

## Cable cost per unit length

| Batt | PDU |
| --- | --- | 
| $1.15 | $0.75 |
 
 In this notebook, an optimization problem will be deployed and solved to find the least costly installation conditions.
