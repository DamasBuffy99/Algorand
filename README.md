# Algorand
It's an Algorand Smart Contract
1-First line takes the fee of a transaction submitted to this contract instance. After that, we introduce a
constant value of 10000, putting it on top of the stack. After that we perform less or equal comparison. This will protect us from setting a fee that is too high.

2-First, take the 0-th (first) argument of the transaction that calls this contract instance, and put it on top of the stack. In our case, the first (and the only)
argument is the secret passphrase string that will unlock the funds in the contract.
Then, calculate the length of this argument and put it in the stack. After that, introduce a constant and compare the length of the argument to find out whether it
is equal to 73. Final line of this snippet performs a logical conjunction of results from executing part in
Listing 1 and Listing 2. Thus, if the fee is less than the threshold and the first argument has length of 73 bytes, the resulting value will be equal to 1.

3-Again, this part of the code takes the first argument from the function call and pushes it to the top of the stack. This time it is hashed with the SHA-256 algorithm.
This opcode takes the top value from the stack and hashes it. The next line loads a constant base64 encoded byte image on the top of the stack. After this both values 
are compared.
This piece of code hashes the provided passphrase string and compares it to the correct hash value. If hashes are equal, the program goes to the next step,
again performing logical conjunction between the latest value with previous conditions.

4-Accounts canreceive coins either via a simple Sender->Receiver transaction or via Sender->Receiver AND Sender->CloseRemainderTo. CloseRemainderTo is used to ‘close’
the sending account and ensures that any ‘remaining’ balance in the sender account is sent to the specified close-to account. The Receiver and Close To are often the
same account, but can be different!
In Listing 4 we take the CloseRemainderTo property and compare it to the Receiver property. If they match and all previous
conditions have been satisfied, funds are unlocked.

