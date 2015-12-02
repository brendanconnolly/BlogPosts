
In this second installment of Testing the Arbitrary we'll take a look at testing a vending machine and create a mind map to record the results. If you are not familiar with mind maps you can take a look at my post [Mind Mapping a Stapler](http://wp.me/p6vwxg-1T) for a brief introduction.

Similar to a stapler, testing a vending machine is another one of random items you might get asked to come up with tests for in an interview.  I think its safe to say at one point or another we've all used a vending machine, but have you ever thought about all the components you would test? It's actually a pretty rich surface for testers to use as a thought experiment. 

![Vending Machine Testing Mind Map](http://www.brendanconnolly.net/wp-content/uploads/2015/12/VendingMachine_map.png)

### Setting Scope
Just saying vending machine is vague, so what kind of vending machine is it? While it's not specifically about soda vs snacks question, it does affect your approach. If a machine sells all items at a single price testing will be different from machines where different items have different prices. 

Asking questions to better understand the domain is a major part of testing. It will also help spark ideas and provide insight into your thought process while testing.    

### Ordering, Payment and Delivery
These are the key functions of a vending machine, if you can't place an order, pay and receive the item then there is good chance you will see customers physically assaulting the device. 

Payments is a trickier subject than you might expect. Even if the machine only accepts coins, there are still the different permutations that will add up to the price required. In reality though when was the last time you've seen people use coins at a vending machine? These days it might even be a rarity that people are actually carrying cash. Many machines today have card readers to allow payments using credit, debit or other cashless solutions. This now introduces a whole new layer of test concerns since the device must have some network connectivity. 

After payment the customer expects the product to be delivered not to be hanging off edge of the display wedged up against the glass. If it's a soda, it can't be so shaken that is sprays everywhere when opened. Delivery also means customers don't get more than they pay for, can items be arranged so they can dislodge nearby products? 

### Security
At some point I think we've all tried to stick our arm up into a vending machine to see if we could grab the goods, maybe shaken the machine a little to see what pops loose. So we need to test to be sure the items are secure and that tampering is prevented. This also extends to making sure that the money is secure. It needs to be secure enough to not pose a physical risk to users. 

If the vending machine takes credit cards there's also a matter of protecting sensitive information. Since it might be network enabled it also needs to be protected from hackers.

### Reporting, Inventory and Stock
There's also the business and administrative side to vending machines. Can owners get any insight into their customers needs? How easily can they tell the profitability of one machine versus another? Do they have to be physically next to a machine to see stock levels or if the machine is offline or needing maintenance? 

How easy is the machine to restock, remove cash or maintain? 

### Wrapping Up
This is only my second attempt at mind mapping and I really think it is a valuable tool. I was never a fan of heavily structured test documentation, it's always felt constraining. To the point where the structure got in the way of the flow of my ideas. If I wanted to change or reorganize my tests I would have a substantial amount of purely administrative work. The tooling for mind maps really offers only minimal friction, I can shift nodes around and reconnect them to different areas easily. 

Test documentation is often billed as a learning / training tool but in practice the main use seems to be for the case of auditing. I see much more value in a mind map as a training tool. The information can be absorbed at a glance or heavily studied. There's just less friction, if mind maps can't replace your test scripts maybe consider using them as a planning tool and linking them to the structured docmentation.   

 

