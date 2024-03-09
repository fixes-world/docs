---
description: 100% on-chain lottery on FIXeS World platform
---

# FIXeS Lottery

> Inspired by [https://www.powerball.com/](https://www.powerball.com/)

### Basic Concept

**Ticket：**&#x20;

You need to participate by purchasing a Lottery Ticket.

**Balls：**

Each ticket contains 5 white balls and 1 red ball. They are all numbers, and the range of numbers:

* White Balls: **1 \~ 33**
* Red Ball: <mark style="color:red;">**1 \~ 16**</mark>

When your tickets matches the winning result according to the rules, you will receive the corresponding prize.

**Prizes and Jackpot:**

The jackpot grows until it is won. Players win a prize by matching one of the 9 ways to win. The jackpot is won by matching all five white balls in any order and the red ball.&#x20;

**PowerUp:**

You can choose to pay more when buying lottery tickets as **PowerUp** to increase the multiplier after winning.&#x20;

Note: The Jackpot is not affected by Powerup and only depends on the current accumulated Jackpot and the number of Jackpot winners.

### Game Pools

Currently, two prize pools are available.

* ID: FIXES\_MINTING\_LOTTERY\_POOL
  * The Prize Token is **$FLOW**.
  * Each ticket price is **1 $FLOW** before **$fixes** are minted out.&#x20;
  * The lottery will be drawn automatically every three days.
  * Each purchase will receive 1 Ticket and mint 4000 **$fixes** at the same time.
  * When $fixes are minted out, the ticket price will remove the cost of **$fixes** minting.
* ID: FIXES\_BASIS\_LOTTERY\_POOL
  * The Prize Token is **$fixes**
  * Each ticket price is **2000 $fixes**
  * The lottery will be drawn automatically every three days.

Note: customized numbers choosing is still WIP, current the number of tickets are generated randomly when purchasing.

For on-chain randomness on Flow, please refer to: [https://flow.com/post/on-chain-randomness-on-flow](https://flow.com/post/on-chain-randomness-on-flow)

### Winning rules

<table><thead><tr><th width="137">PrizeRank</th><th width="223">Match Rule</th><th width="212">Prize</th><th>Service fee</th></tr></thead><tbody><tr><td>JACKPOT</td><td>5 White + 1 <mark style="color:red;">Red</mark></td><td><strong>Grant Prize</strong></td><td>16%</td></tr><tr><td>SECOND</td><td>5 White</td><td><mark style="color:green;"><strong>50000</strong></mark> x <strong>TicketPrice</strong></td><td>16%</td></tr><tr><td>THIRD</td><td>4 White + 1 <mark style="color:red;">Red</mark></td><td><mark style="color:green;"><strong>5000</strong></mark> x <strong>TicketPrice</strong></td><td>16%</td></tr><tr><td>FOURTH</td><td>4 White / 3 White + 1 <mark style="color:red;">Red</mark></td><td><mark style="color:green;"><strong>25</strong></mark> x <strong>TicketPrice</strong></td><td>0%</td></tr><tr><td>FIFTH</td><td>3 White / 2 White + 1 <mark style="color:red;">Red</mark></td><td><mark style="color:green;"><strong>4</strong></mark> x <strong>TicketPrice</strong></td><td>0%</td></tr><tr><td>SIXTH</td><td>1 White + 1 Red / 1 <mark style="color:red;">Red</mark></td><td><mark style="color:green;"><strong>2</strong></mark> x <strong>TicketPrice</strong></td><td>0%</td></tr></tbody></table>

The Prize of Jackpot, Second, and Third will be deducted by a certain Service Fee.

The Service Fee will be injected into the platform's Treasury Pool or Staking Pool.

* For $FLOW Lottery, 8% Service Fee will be deposit to $FLOWS Staking Pool and 8% Service Fee will be deposit to platform treasury
* For $𝔉rc20 Lottery, 16% Service Fee will be deposit to $FLOWS Staking Pool
