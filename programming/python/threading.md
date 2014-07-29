# python threading
because of GIL (global interpreter lock) python multithreading is not real multithreading.
only one thread is executed at any time.

use threads to decouple blocking operations.

do _not_ use threads for computationally expensive work. 
