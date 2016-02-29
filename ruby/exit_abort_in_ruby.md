###exit. exit!, abort in ruby

In short:

    Kernel.exit(code) "exits" the script immediatelly and return the code to the OS; however, just before doing it, it calls any registered at_exit handler that your code could have registered
    Kernel.exit!(code) does the same, but exits immediatelly, no at_exit handlers called
    Kernel.abort(message) takes a message that will be printed to STDERR just before exiting with a failure code=1

