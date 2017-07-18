<!-- $theme: default -->

# Testing a Token with more than examples

## Stateful property-based testing of smart contracts

Nicolás Berger - Co-founder & Engineer, <strong>Winding Tree</strong>

<br />
<br />

<div style="text-align:center" ><img src="wt.png" /></div>

---
<!-- page_number: true -->
<!-- footer: @nberger - @WindingTree -->

# Winding Tree

A decentralized marketplace for travel

ICO (Initial Coin Offering): mid-September

Reverse dutch auction crowdsale

---

# Limitations of testing by example

- Just the examples the programmer come up with

```
assert.equal(5, sum(2, 3))
assert.equal(5, sum(1, 4))
```

---

# Limitations of testing by example

- Just the examples the programmer come up with

```
assert.equal(5, sum(2, 3))
assert.equal(5, sum(1, 4))

function sum(x,y) {
  return 5;
}
```

---

# Limitations of testing by example

- Too many combinations

  - submitBid -> submitBid -> presalePayment -> submitBid ...
  - presalePayment -> submitBid -> presalePayment ...
  - submitBid -> wait -> wait -> submitBid ...
  - wait -> submitBid -> [...] -> presalePayment -> submitBid
---

# Property-based testing

- Generators: generate random input
- Run: Verify that property holds true on every input
- Shrink: Find the smallest input that still fails

---

# Smart contracts

- State
  - stage: Stopped / Running / Finished
  - bids: [{account: xyz, tokens: 42, price: 2.7}, ...]
  - presalePayments: [{account: abc, ether: 4}, {...}]
  - ...

---

# Stateful Property-based testing

- Generate sequence of transactions
- Apply transactions on the smart contracts
- Compare actual state to expected state
- Find the shortest sequence that still fails
  - wait -> wait -> wait -> wait -> submitBid

---

# How to find properties

- Mathematical
  ```
  a + b == b + a // commutative
  ```
- Round tripping / inverse
  ```
  s == fromJSON(toJSON(s))
  ```
- Idempotence 
  ```
  update(user) == update(update(user))
  ```
- Function equality
  ```
  sort(arr) == fastSort(arr)
  ```
  
---

# Tools we use

- <strong>Truffle</strong>: development framework for Ethereum 
- <strong>testrpc</strong>: Fast Ethereum RPC client for testing and development
- <strong>JSVerify</strong>: Javascript property-based testing library

---
# Links

John Hughes - Testing the Hard Stuff and Staying Sane
https://www.youtube.com/watch?v=zi0rHwfiX1Q

JSVerify - Property-based testing for javascript http://jsverify.github.io/

Adding property-based tests for Winding Tree smart contracts https://github.com/windingtree/LifToken/pull/60

An introduction to property-based testing
https://fsharpforfunandprofit.com/posts/property-based-testing/

---

<!-- page_number: false -->
<!-- footer: -->

# Thanks!

## Questions?

</br>
</br>

<img src="github.png" height="24" /> nberger
<img src="twitter.png" height="24" /> nicoberger


<div style="text-align:center" >
  <img src="wt.png" />
  <br />
  <a href="https://windingtree.com">windingtree.com</a>
  <br/>
  <a href="https://windingtree.com">slack.windingtree.com</a>
</div>