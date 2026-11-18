# What is an oracle?
"Oracle" is the name used for iterator puppets in code. It is not to be confused with an iterator as a whole, which usually encompasses an entire region, while an oracle is only the part that you directly interact with in its chamber.
This wiki also uses the term "oracle" to refer to objects representing the puppet in code, i.e. objects extending the `Oracle` class.
"Broken" is also used in this wiki to refer to oracles which have collapsed, like Looks to the Moon (post-Spearmaster) and Five Pebbles (for Saint)
# What is this library?
LibOracle is a code dependency that provides a higher level of abstraction to the multitude of convoluted classes involved in the creation of oracles, thus greatly simplifying the process.
The core philosophy of this library is to provide a solid foundation, on top of which you can build your creation, rather than having to untangle a mountain of spaghetti every time you want to do something.
This means that the library itself provides little to no implicit behavior, only tools to write that behavior yourself. As such this is **not** a replacement for [IteratorKit](https://steamcommunity.com/sharedfiles/filedetails/?id=3072891344) or [Iterator Creator](https://steamcommunity.com/sharedfiles/filedetails/?id=3558121337), because you still have to write custom code.
In cases where it's necessary to provide implicit behavior, it can in most cases be overridden by the extending class.
# Is this vibecoded?
No.
If you really want to make sure, check out the [GitHub repo](https://github.com/hexahedron1/LibOracle).