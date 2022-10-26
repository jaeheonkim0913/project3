High level approach:
The script first sends a hello message, and receives back message to be carried out.
The type of message can be:
update in which the routing table is updated and such update is announced to corresponding neighbors that are necessary to be updated.
withdraw which saves a copy of the revocation message and then update/aggregate the routing table as necessary
data which sends the data to the corresponding destination with longest prefix match after finding the best route. It also makes sure the source/destination is a customer, as if they are not, the data is dropped.
dump which is mostly just for testing, sends the routing table to the source of the message, except expanded to hold each route in a single item.

challenges:
Figuring out how to filter a list of routes to find the best route possible in when sending data was pretty difficult at first. I had to do a lot of bug fixing to make sure routes weren't being removed from the potential list of routes unknowingly.
Aggregating the routing table was also difficult, as figuring out how to check neighbor adjacency was a little bit confusing at first. I got some help from google.
Converting between ipv4 to bin and vice versa was also a bit difficult at first, as the parsing was not happening as intended.

Design features:
I think the function bestRoute is neatly written, I had to brush up on how to use lambda functions to nicely filter the list of possible routes. Not too difficult, but cool to write once I had the longest prefix filter written.

Testing:
I just simply used the run command on the given config files over and over again and checked error messages on gradescope.
