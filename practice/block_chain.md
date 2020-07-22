{{{
https://medium.com/@vanflymen/learn-blockchains-by-building-one-117428612f46
What does a Block look like?
Each Block has an index, a timestamp (in Unix time), a list of transactions, 
a proof (more on that later), and the hash of the previous Block.
Adding Transactions to a Block
After new_transaction() adds a transaction to the list, it returns the index
of the block which the transaction will be added to—the next one to be mined. 
This will be useful later on, to the user submitting the transaction.
Creating new Blocks
When our Blockchain is instantiated we’ll need to seed it with a genesis block—a block 
with no predecessors. We’ll also need to add a “proof” to our genesis block which 
is the result of mining (or proof of work). 
A Proof of Work algorithm (PoW) is how new Blocks are created or mined on the blockchain. 
The goal of PoW is to discover a number which solves a problem. The number must be 
difficult to find but easy to verify—computationally speaking—by anyone on the network. 
This is the core idea behind Proof of Work.
Let’s decide that the hash of some integer x multiplied by another y must end in 0. 
So, hash(x * y) = ac23dc...0. And for this simplified example, let’s fix x = 5. Implementing this in Python:

from hashlib import sha256x = 5
y = 0  # We don't know what y should be yet...while sha256(f'{x*y}'.encode()).hexdigest()[-1] != "0":
    y += 1print(f'The solution is y = {y}')
The solution here is y = 21. Since, the produced hash ends in 0:

hash(5 * 21) = 1253e9373e...5e3600155e860
In Bitcoin, the Proof of Work algorithm is called Hashcash. 
}}}
