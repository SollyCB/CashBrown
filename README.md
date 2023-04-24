# REVIEW IF YOU WANT TO USE!

**This was implemented largely as the baby steps towards some Vulkan engine shizzle, I am convinced that the implementation is decent and works well (as it is simply a port) but it has not been extensively tested and there is one loop that I imagine could run faster (maybe) with benchmarking. It is not heavily benchmarked to check each piece of the implementation, but it is basically a one to one port, so I doubt it is digustingly wrong (I am a noob, and this is not heavily tested, so I could be wrong). I just wanted this out there because I am pleased with this, I would welcome review and criticism. There is only basic functionality: you can insert, get, and the map rehashes and grows if it has insufficient space. I think basically everything else builds on these primitives.**

It also uses a custom allocator (custom is an overstatement, really just a wrapper around Matthew Conte's tlsf C implementation - I wanted TCmalloc but tests failed 
on my laptop), but this is only used for three mallocs and a free, so a search and replace can be done for std allocator, (not anyone will ever read this :D). 

Review is welcome <3 

## C++ Port of the Rust HashBrown hashmap

The most basic functionality is implemented, it compiles on my linux laptop, I have not ported to Windows, but from memory nothing is GCC specific (not tested sry).

Uses SIMD instructions, not 32-bit portable, (uses size_t in ways that I think fails on 32 bit). 

Map has a minimum size of 16 bytes for control, plus 16 * sizeof(T). This could be shrunk, but for smtg as memory hog as a hashmap, intended my usage, this is 
inconsequential.

*I apologise for any dissatisfaction with the map, I was pleased when it worked, so I put it here. I have such an empty github that its nice to have smtg cool...*

### TODO:
I would love to make another version which is concurrent like the Java/Gjengset Rust map, but I am not a HashMap enthusiast, it was just an exercise for source code 
reading and growing my brain.
