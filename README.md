Some time ago I wanted to try tensorflow, but I hit [this](https://github.com/tensorflow/tensorflow/issues/17411) issue. Basically my workstation is quite old and the cpu doesn't support AVX instructions, required by recent tensorflow versions. 

Importing tensorflow gave me: 

    Illegal instruction (core dumped)

The proposed solution is to do a downgrade to an older version, but if you want to benefit of the new features, you have to find alternatives, like compiling it on your workstation.

Since I couldn't find a pre-built package compiled without AVX support, I built my own and now I make it available.
The package has been build on a **Intel Core Duo P8400**.
The tensorflow version I built is 1.10.

Here's what's supported by my notebook.

Command:

    gcc -march=native -Q --help=target

Output: 

    The following options are target specific:
      -m128bit-long-double        		[enabled]
      -m16                        		[disabled]
      -m32                        		[disabled]
      -m3dnow                     		[disabled]
      -m3dnowa                    		[disabled]
      -m64                        		[enabled]
      -m80387                     		[enabled]
      -m8bit-idiv                 		[disabled]
      -m96bit-long-double         		[disabled]
      -mabi=                      		sysv
      -mabm                       		[disabled]
      -maccumulate-outgoing-args  		[disabled]
      -maddress-mode=             		long
      -madx                       		[disabled]
      -maes                       		[disabled]
      -malign-data=               		compat
      -malign-double              		[disabled]
      -malign-functions=          		0
      -malign-jumps=              		0
      -malign-loops=              		0
      -malign-stringops           		[enabled]
      -mandroid                   		[disabled]
      -march=                     		core2
      -masm=                      		att
      -mavx                       		[disabled]
      -mavx2                      		[disabled]
      -mavx256-split-unaligned-load 	[disabled]
      -mavx256-split-unaligned-store 	[disabled]
      -mavx5124fmaps              		[disabled]
      -mavx5124vnniw              		[disabled]
      -mavx512bw                  		[disabled]
      -mavx512cd                  		[disabled]
      -mavx512dq                  		[disabled]
      -mavx512er                  		[disabled]
      -mavx512f                   		[disabled]
      -mavx512ifma                		[disabled]
      -mavx512pf                  		[disabled]
      -mavx512vbmi                		[disabled]
      -mavx512vl                  		[disabled]
      -mavx512vpopcntdq           		[disabled]
      -mbionic                    		[disabled]
      -mbmi                       		[disabled]
      -mbmi2                      		[disabled]
      -mbranch-cost=              		3
      -mcld                       		[disabled]
      -mclflushopt                		[disabled]
      -mclwb                      		[disabled]
      -mclzero                    		[disabled]
      -mcmodel=                   		[default]
      -mcpu=                      		
      -mcrc32                     		[disabled]
      -mcx16                      		[enabled]
      -mdispatch-scheduler        		[disabled]
      -mdump-tune-features        		[disabled]
      -mf16c                      		[disabled]
      -mfancy-math-387            		[enabled]
      -mfentry                    		[disabled]
      -mfma                       		[disabled]
      -mfma4                      		[disabled]
      -mforce-drap                		[disabled]
      -mfp-ret-in-387             		[enabled]
      -mfpmath=                   		sse
      -mfsgsbase                  		[disabled]
      -mfunction-return=          		keep
      -mfused-madd                		
      -mfxsr                      		[enabled]
      -mgeneral-regs-only         		[disabled]
      -mglibc                     		[enabled]
      -mhard-float                		[enabled]
      -mhle                       		[disabled]
      -miamcu                     		[disabled]
      -mieee-fp                   		[enabled]
      -mincoming-stack-boundary=  		0
      -mindirect-branch-register  		[disabled]
      -mindirect-branch=          		keep
      -minline-all-stringops      		[disabled]
      -minline-stringops-dynamically 	[disabled]
      -mintel-syntax              		
      -mlarge-data-threshold=<number> 	65536
      -mlong-double-128           		[disabled]
      -mlong-double-64            		[disabled]
      -mlong-double-80            		[enabled]
      -mlwp                       		[disabled]
      -mlzcnt                     		[disabled]
      -mmemcpy-strategy=          		
      -mmemset-strategy=          		
      -mmitigate-rop              		[disabled]
      -mmmx                       		[enabled]
      -mmovbe                     		[disabled]
      -mmpx                       		[disabled]
      -mms-bitfields              		[disabled]
      -mmusl                      		[disabled]
      -mmwaitx                    		[disabled]
      -mno-align-stringops        		[disabled]
      -mno-default                		[disabled]
      -mno-fancy-math-387         		[disabled]
      -mno-push-args              		[disabled]
      -mno-red-zone               		[disabled]
      -mno-sse4                   		[disabled]
      -mnop-mcount                		[disabled]
      -momit-leaf-frame-pointer   		[disabled]
      -mpc32                      		[disabled]
      -mpc64                      		[disabled]
      -mpc80                      		[disabled]
      -mpclmul                    		[disabled]
      -mpcommit                   		[disabled]
      -mpku                       		[disabled]
      -mpopcnt                    		[disabled]
      -mprefer-avx128             		[disabled]
      -mpreferred-stack-boundary= 		0
      -mprefetchwt1               		[disabled]
      -mprfchw                    		[disabled]
      -mpush-args                 		[enabled]
      -mrdpid                     		[disabled]
      -mrdrnd                     		[disabled]
      -mrdseed                    		[disabled]
      -mrecip                     		[disabled]
      -mrecip=                    		
      -mrecord-mcount             		[disabled]
      -mred-zone                  		[enabled]
      -mregparm=                  		6
      -mrtd                       		[disabled]
      -mrtm                       		[disabled]
      -msahf                      		[enabled]
      -msgx                       		[disabled]
      -msha                       		[disabled]
      -mskip-rax-setup            		[disabled]
      -msoft-float                		[disabled]
      -msse                       		[enabled]
      -msse2                      		[enabled]
      -msse2avx                   		[disabled]
      -msse3                      		[enabled]
      -msse4                      		[disabled]
      -msse4.1                    		[enabled]
      -msse4.2                    		[disabled]
      -msse4a                     		[disabled]
      -msse5                      		
      -msseregparm                		[disabled]
      -mssse3                     		[enabled]
      -mstack-arg-probe           		[disabled]
      -mstack-protector-guard=    		tls
      -mstackrealign              		[disabled]
      -mstringop-strategy=        		[default]
      -mstv                       		[enabled]
      -mtbm                       		[disabled]
      -mtls-dialect=              		gnu
      -mtls-direct-seg-refs       		[enabled]
      -mtune-ctrl=                		
      -mtune=                     		core2
      -muclibc                    		[disabled]
      -mveclibabi=                		[default]
      -mvect8-ret-in-mem          		[disabled]
      -mvzeroupper                		[enabled]
      -mx32                       		[disabled]
      -mxop                       		[disabled]
      -mxsave                     		[disabled]
      -mxsavec                    		[disabled]
      -mxsaveopt                  		[disabled]
      -mxsaves                    		[disabled]
    
      Known assembler dialects (for use with the -masm= option):
        att intel
    
      Known ABIs (for use with the -mabi= option):
        ms sysv
    
      Known code models (for use with the -mcmodel= option):
        32 kernel large medium small
    
      Valid arguments to -mfpmath=:
        387 387+sse 387,sse both sse sse+387 sse,387
    
      Known indirect branch choices (for use with the -mindirect-branch=/-mfunction-return= options):
        keep thunk thunk-extern thunk-inline
    
      Known data alignment choices (for use with the -malign-data= option):
        abi cacheline compat
    
      Known vectorization library ABIs (for use with the -mveclibabi= option):
        acml svml
    
      Known address mode (for use with the -maddress-mode= option):
        long short
    
      Known stack protector guard (for use with the -mstack-protector-guard= option):
        global tls
    
      Valid arguments to -mstringop-strategy=:
        byte_loop libcall loop rep_4byte rep_8byte rep_byte unrolled_loop vector_loop
    
      Known TLS dialects (for use with the -mtls-dialect= option):
        gnu gnu2


 

