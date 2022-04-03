## Defi or Defi2

whats happend after `defi` move to `defi2` AND wha is defi2 at all!

the concept of own banking system and control to own assets by using blockchain technology is ***defi***.

***defi2*** is: more security concept, anonymously concept on transactions.

**so if we need more trust, need more security**. then the new concept of ***defi(decentralized finance)*** come to help us, the defi2. defi2 just a name, not new. in a code by example i teach you how it work.

in `solidity` (ethereum base smartcontract language) you can withdraw your asset. look at this example:

```
function withdraw() public noReentrant onlyowner { 

  (bool success, ) = msg.sender.call{value: address(this).balance}(""); 

  require(success); 

}
```

at this code the owner of contract can withdraw ***ERC20 Native asset***. but not anonymous and in normal security by using a modifier called `noReentrant`. 

now if you want more security you can add some codes to make/generate password. a hash code generated 1way, and can not decrypt by using a function of solidity “keccak256” (in family of ‘sha256’) . then you can only withdraw by using the real password.

look at this code for example:

```
function withdraw(string memory password) public noReentrant {

  require(gen(password) == hashedPass, "Access denied!");

  (bool success, ) = msg.sender.call{value: address(this).balance}("");

  require(success);

}

function gen(string memory pas) internal pure returns (bytes16 _pasGen) {

  _pasGen = bytes16(keccak256(abi.encodePacked(pas)));

}
```

` example: 0xfb39401d483e3b8ed34e9d5cb7b345ab <- mosi-sol `

source at: [github/mosi-sol](https://github.com/mosi-sol/live-contracts/tree/main/episode-20) (my github repo for solidity language)

in this code we made our own password, and can withdraw by that generated hash password for withdrawing our asset. [attention: this code is example and not full yet, just for this article].

now if you as BOB send the password to ALICE, then alice can withdraw assets, because you approve her for withdrawing just by sending a password (the ZERO KNOWLEDGE PROOF concept).

welcome to the new wonderfull world of technology by using decentalization concept.

