
As @LeVraiGG already states, the answer is here: https://github.com/golang/go/wiki/MacOS12BSDThreadRegisterIssue. The programme needs a newer go version, so the programme in question must be updated.

For me the error occured with the programme docker-machine. What I had to do was upgrade docker-machine and link the new version:

Upgrade docker-machine: brew install docker-machine
Run brew install docker-machine again to see if it is linked. If not, continue
Remove old link rm /usr/local/bin/docker-machine
Link new version brew link docker-machine
So I guess with the other failing programmes, the process could be similar




vinodkumar@Vinods-MacBook-Air atsea-sample-shop-app % docker-machine 
fatal error: runtime: bsdthread_register error

runtime stack:
runtime.throw(0x20594e0, 0x21)
	/usr/local/go/src/runtime/panic.go:619 +0x81 fp=0x7ff7bfeff198 sp=0x7ff7bfeff178 pc=0x1029751
runtime.goenvs()
	/usr/local/go/src/runtime/os_darwin.go:129 +0x83 fp=0x7ff7bfeff1c8 sp=0x7ff7bfeff198 pc=0x10272d3
runtime.schedinit()
	/usr/local/go/src/runtime/proc.go:496 +0xa4 fp=0x7ff7bfeff220 sp=0x7ff7bfeff1c8 pc=0x102c014
runtime.rt0_go(0x7ff7bfeff258, 0x1, 0x7ff7bfeff258, 0x0, 0x1000000, 0x1, 0x7ff7bfeff400, 0x0, 0x7ff7bfeff40f, 0x7ff7bfeff42b, ...)
	/usr/local/go/src/runtime/asm_amd64.s:252 +0x1f4 fp=0x7ff7bfeff228 sp=0x7ff7bfeff220 pc=0x1052c64
vinodkumar@Vinods-MacBook-Air atsea-sample-shop-app % eval "$(docker-machine env -u)"
fatal error: runtime: bsdthread_register error

runtime stack:
runtime.throw(0x20594e0, 0x21)
	/usr/local/go/src/runtime/panic.go:619 +0x81 fp=0x7ff7bfeff188 sp=0x7ff7bfeff168 pc=0x1029751
runtime.goenvs()
	/usr/local/go/src/runtime/os_darwin.go:129 +0x83 fp=0x7ff7bfeff1b8 sp=0x7ff7bfeff188 pc=0x10272d3
runtime.schedinit()
	/usr/local/go/src/runtime/proc.go:496 +0xa4 fp=0x7ff7bfeff210 sp=0x7ff7bfeff1b8 pc=0x102c014
runtime.rt0_go(0x7ff7bfeff240, 0x3, 0x7ff7bfeff240, 0x1000000, 0x3, 0x7ff7bfeff3f8, 0x7ff7bfeff407, 0x7ff7bfeff40b, 0x0, 0x7ff7bfeff40e, ...)
	/usr/local/go/src/runtime/asm_amd64.s:252 +0x1f4 fp=0x7ff7bfeff218 sp=0x7ff7bfeff210 pc=0x1052c64