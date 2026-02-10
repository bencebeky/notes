# disk

## hard disk drives

* seek time due to head movement: 8~10 ms, down to 4 ms for 7200 rpm
* rotational latency
* read and write entire sectors
* sequential I/O cheaper

## solid state drives

* memory cell, string, array, page, blocks, plane, die, package, SSD
* page can be read/written, block can be erased
* 0.1 ms

## why do we care

* there is a smallest unit of read/write
* many algorithms were developed for HDDs, later for SSDs

# B-trees

## binary search tree

every node has a value, every node it its left subtree has lower values, every
node in its right subtree has higher values

balanced tree: leaves on at most two adjacent levels

rebalancing by rotating

low fanout: many nodes visited, many reads and indirections

paged trees: put large contiguous chunks on a page each

## B-tree

Root and internal nodes have N+1 slots for children and N separator keys
leaf nodes have N slots for keys. Typically so large that nodes fill up a page.

Technically B trees may hold complete data fields in any node. They are also
called multiway trees.

B+ trees only hold data fields in leaf nodes, other nodes only have separator
keys. These are so common that people typically call them B trees, including in
this book.

2-3-trees are just a special case. so are binary trees.

## management

overflowing nodes may be split, with one key promoted to the parent, which may
also split.

underflowing nodes may be merged.

alternatively, overflow and underflow may trigger moving children around to/from
sibling nodes if possible, which is more complex, but results in higher or
better distributed occupancy
