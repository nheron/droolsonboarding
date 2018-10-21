# Requirements

We are working for a retail company that buys its products from different places in Asia mostly.  Each shop can go to the buying web site and say what he wants and put an order.  Up to now, the transport cost was estimated but not calculated on the content of the order.   

The purpose is to implement such a calculator.

## Data model

A customer puts an order that contains products. An order contains a lot of products with a number.  
A product has

* a name
* a height, 
* a width, 
* a depth, 
* transport type : if the product can be put with other products in a pallet, individual \(alone\) or bulk \(like sand for example\)
* a weight

A product can be put on a pallet. A pallet is 120 cm width and and 80 cm depth. It can be a maximum of 2 meters in height and the weight should not exceed 1400 kg. We should use a simple algorithm to fill each pallet. It will not be optimized, but we should use that as an upper limit for the costs.  A product that is bigger than 60 cm in width or depth or higher than 1m should be put alone on a pallet.

All products start from the same city and go to the same city in an order. A trip is composed of steps. Each step can be done by train, boat or truck.

Here is the list of products in our test order.

| Product | Transport type | Number | Height | Width | Depth | Weight |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Drill | pallet | 1000 | 20cm | 40cm | 30cm | 2 kg |
| Screwdriver | pallet | 30000 | 3cm | 2cm | 20cm | 0,2 kg |
| Sand | bulk |  |  |  |  | 35 Tons |
| Gravel | bulk |  |  |  |  | 14 Tons |
| Furniture | individual | 23 |  |  |  | 500 kg |

And the trip is as follows:

| \# | start city | arrival city | distance \(km\) | travel mode |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Shangai | Rotterdam | 22000 | Boat |
| 2 | Rotterdam | Tournai | 300 | Train |
| 3 | Tournai | Lille | 20 | Truck |

There are 3 types of costs:

* Transport costs per Pallet

| Transport | Cost |
| :--- | :--- |
| Boat | 0,2€\/km |
| Train | 0,5€\/km |
| Truck | 1€\/km |

* Taxes

| City | Cost |
| :--- | :--- |
| Shangai | 0,02€\/kg |
| Rotterdam | 0,05€\/kg and 1€ per handling person |
| Tournai | 2€ per handling person |
| Lille | 30€ per handling person |

* Handling

| City | Cost |
| :--- | :--- |
| Shangai | 20€\/hour and a person can handle 13 pallets\/hour |
| Rotterdam | 45€\/hour and a person can handle 60 pallets\/hour |
| Tournai | 67€\/hour and a person can handle 40 pallets\/hour |
| Lille | 79€\/hour and a person can handle 30 pallets\/hour |

The handling should not take more than 12 hours per city.

The source code and the solution can be found [here](https://github.com/nheron/droolscourse/tree/master/cost-calculation).

