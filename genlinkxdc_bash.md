# genlink xdc bash

```bash
#!/bin/bash
#will @20211110  
#this bash is used to genenrate windows gen xdc bat.

#declare -a f-gtclks=(225 226 220 231)  #defualt

declare -a f1gtclks=(225 227 220 231)
declare -a f1quads=(224 229 225 227 231 220 219 230)
declare -a f1fpgas=(2 3 4 5 6 7 9 12)
declare -a f1fpgas2=(0 0 0 0 0 0 0 0)
declare -a f1seqs=(0 1 2 3 4 5 6 8)

declare -a f2gtclks=(224 226 219 232)
declare -a f2quads=(224 219 232 226)
declare -a f2fpgas=(1 7 12 13)
declare -a f2fpgas2=(0 0 0 0)
declare -a f2seqs=(0 1 2 3)

declare -a f3gtclks=(224 227 220 230)
declare -a f3quads=(232 229 227 224 219 221 230 220)
declare -a f3fpgas=(7 1 4 6 20 8 4 5)
declare -a f3fpgas2=(0 0 0 0 0 0 0 0)
declare -a f3seqs=(0 1 2 3 4 5 6 7)

declare -a f4gtclks=(225 227 220 231)
declare -a f4quads=(225 227 219 224 232 229 221 220 230 1231)
declare -a f4fpgas=(1 3 3 5 5 6 9 10 15 20)
declare -a f4fpgas2=(0 0 0 0 0 0 0 0 0 0)
declare -a f4seqs=(0 1 2 3 4 5 6 7 8 9)

declare -a f5gtclks=(224 227 220 231)  
declare -a f5quads=(224 220 227 232 231 221 230)
declare -a f5fpgas=(4 8 1 7 3 4 20)
declare -a f5fpgas2=(0 0 0 0 0 0 0)
declare -a f5seqs=(0 1 2 3 4 5 6)

declare -a f6gtclks=(224 225 220 231)  
declare -a f6quads=(231 230 229 232 224 1221 220 219)
declare -a f6fpgas=(9 9 4 1 3 20 11 15)
declare -a f6fpgas2=(0 0 0 0 0 0 10 17)
declare -a f6seqs=(0 1 2 3 4 5 7 8)

#GPIM(J8)
declare -a f7gtclks=(225 226 220 231)  
declare -a f7quads=(220 231 1232 226 230 219 224 225 221 229)
declare -a f7fpgas=(3 1 20 5 16 2 8 12 13 9)
declare -a f7fpgas2=(0 0 0 0 18 0 0 0 14 0)
declare -a f7seqs=(0 1 2 3 4 5 6 7 8 9)

declare -a f8gtclks=(224 225 220 230)  
declare -a f8quads=(220 225 224 230)
declare -a f8fpgas=(5 9 7 3)
declare -a f8fpga2=(0 0 0 0)
declare -a f8seqs=(1 2 3 6)

#gtclk 226 not used!
declare -a f9gtclks=(225 0 220 231)  
declare -a f9quads=(219 220 221 1232 224 225 229 231)
declare -a f9fpgas=(6 6 4 20 11 8 7 1)
declare -a f9fpgas2=(0 0 0 0 0 0 0 0)
declare -a f9seqs=(0 1 2 3 4 6 7 8)

#sfp+(J7)
#gtclk 226 , 231 not used!
declare -a f10gtclks=(224 0 220 0)  
declare -a f10quads=(219 224 1220)
declare -a f10fpgas=(4 11 6)
declare -a f10fpgas2=(0 0 0)
declare -a f10seqs=(0 1 2)

declare -a f11gtclks=(225 227 220 230)  
declare -a f11quads=(221 1220 225 219 230 224 227)
declare -a f11fpgas=(17 6 17_d2 9 15 10 12)
declare -a f11fpgas2=(0 0 0 0 0 0 0)
declare -a f11seqs=(0 1 2 3 4 6 7)

#
declare -a f12gtclks=(225 0 220 231)  
declare -a f12quads=(219 231 220 225 221 230)
declare -a f12fpgas=(7 1 2 11 16 18)
declare -a f12fpgas2=(0 0 0 0 0 0)
declare -a f12seqs=(0 1 2 3 4 5)

declare -a f13gtclks=(0 226 219 0)  
declare -a f13quads=(1219 226)
declare -a f13fpgas=(7 2)
declare -a f13fpgas=(0 0)
declare -a f13seqs=(0 2)

declare -a f14gtclks=(0 0 220 0)  
declare -a f14quads=(1220 219)
declare -a f14fpgas=(7 16)
declare -a f14fpgas=(0 0)
declare -a f14seqs=(0 1)

declare -a f15gtclks=(0 0 220 232)  
declare -a f15quads=(221 232 1220 219)
declare -a f15fpgas=(4 11 6 17)
declare -a f15fpgas2=(4 11 6 17)
declare -a f15seqs=(0 1 2 3)

declare -a f16gtclks=(0 0 220 232)  
declare -a f16quads=(1219 232 220 221)
declare -a f16fpgas=(7 14 12 16_d2)
declare -a f16fpgas2=(0 0 0 0)
declare -a f16seqs=(0 1 2 3)

#
declare -a f17gtclks=(0 0 220 230)  
declare -a f17quads=(230 1220 232)
declare -a f17fpgas=(11 6 15)
declare -a f17fpgas=(0 0 0)
declare -a f17seqs=(0 1 2)

# DDR 
# if gtquads <- (1000,2000) ,use the '20' param!
declare -a f18gtclks=(0 0 219 0)  
declare -a f18quads=(1219 221)
declare -a f18fpgas=(7 12)
declare -a f18fpgas2=(0 0)
declare -a f18seqs=(0 1)

#
declare -a f20gtclks=(225 227 220 232)  
declare -a f20quads=(227 224 232 225 220)
declare -a f20fpgas=(4 5 3 9 17)
declare -a f20fpgas2=(6 0 0 7 0)
declare -a f20seqs=(0 1 2 4 5)

#
declare -a fseqs=(1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 20)  
#---------------------------------------------------------------------------------------

#for ID in `seq 1 1` ; do
for ID in ${fseqs[@]} ; do

	echo "">h3_f${ID}.bat
	echo "@echo off">>h3_f${ID}.bat
	echo "%~d1">>h3_f${ID}.bat
	echo "cd %~p1">>h3_f${ID}.bat
	echo "cd %1">>h3_f${ID}.bat
	echo ":: will update @ 20211110">>h3_f${ID}.bat
	echo "echo //------ >h3_f${ID}.di">>h3_f${ID}.bat
	echo "echo // >>h3_f${ID}.di">>h3_f${ID}.bat
	echo "echo // >>h3_f${ID}.di">>h3_f${ID}.bat

	echo "echo open h3_f${ID}.xdc >>h3_f${ID}.di">>h3_f${ID}.bat
	echo "echo wrsub >>h3_f${ID}.di">>h3_f${ID}.bat
	
	echo "echo wrnote #---gclk[use-gclk6-of-vuls440]---  >>h3_f${ID}.di">>h3_f${ID}.bat
	echo "echo wrgck 106 pin_clk _4m >>h3_f${ID}.di">>h3_f${ID}.bat
	
	echo "echo wrnote #---grst[use-grst1-of-vuls440]---         >>h3_f${ID}.di">>h3_f${ID}.bat
    echo "echo wrgrst 11 rst_n                                  >>h3_f${ID}.di">>h3_f${ID}.bat 
    
	#f1gtclks
    fgtclks_tmp0=f${ID}gtclks[0]
    fgtclks_t0=${!fgtclks_tmp0}

    fgtclks_tmp1=f${ID}gtclks[1]
    fgtclks_t1=${!fgtclks_tmp1}

	fgtclks_tmp2=f${ID}gtclks[2]
    fgtclks_t2=${!fgtclks_tmp2}

	fgtclks_tmp3=f${ID}gtclks[3]
    fgtclks_t3=${!fgtclks_tmp3}

    #
	echo "echo wrnote #---gtclk(${fgtclks_t0}-0)(${fgtclks_t1}-0)(${fgtclks_t2}-0)(${fgtclks_t3}-0)---  >>h3_f${ID}.di">>h3_f${ID}.bat 
	if [[ ${fgtclks_t0} != 0 ]] ; then
	  echo "echo wrgtclk ${fgtclks_t0} pin ref1_122m88                      >>h3_f${ID}.di">>h3_f${ID}.bat   
    fi
	if [[ ${fgtclks_t1} != 0 ]] ; then
	  echo "echo wrgtclk ${fgtclks_t1} pin ref2_122m88                      >>h3_f${ID}.di">>h3_f${ID}.bat       
    fi
	if [[ ${fgtclks_t2} != 0 ]] ; then
	  echo "echo wrgtclk ${fgtclks_t2} pin ref_122m88                       >>h3_f${ID}.di">>h3_f${ID}.bat      
  	fi
	if [[ ${fgtclks_t3} != 0 ]] ; then
	  echo "echo wrgtclk ${fgtclks_t3} pin ref3_122m88                      >>h3_f${ID}.di">>h3_f${ID}.bat             
	fi
	#
	for QUAD in `seq 0 11` ; do
	
	    fquads_tmp=f${ID}quads[${QUAD}]
        fquads_t=${!fquads_tmp}
	    if [ ! ${fquads_t}  ] ;  then
                  echo "${QUAD},end for!"
	          break;
	    fi
	
            echo ${fquads_t}
	    #
        ffpgas_tmp=f${ID}fpgas[${QUAD}]
        ffpgas_t=${!ffpgas_tmp}

        fseqs_tmp=f${ID}seqs[${QUAD}]
        fseqs_t=${!fseqs_tmp}


        ffpgas_tmp2=f${ID}fpgas2[${QUAD}]
        ffpgas_t2=${!ffpgas_tmp2}

        if [[ ${ffpgas_t2} -eq 0 ]] ; then
          
		 if [[ ${fquads_t} -gt 1000 ]] ; then
         #half cable,rx  
		   fquads_t=$(( ${fquads_t} - 1000))
           echo "echo wrgtlanes ${fquads_t} pin_sds_chn?_rxp_xi_sv${fseqs_t}_f${ffpgas_t}_f${ID} 20 >>h3_f${ID}.di">>h3_f${ID}.bat  
           echo "echo wrgtlanes 1${fquads_t} pin_sds_chn?_txp_xo_sv${fseqs_t}_f${ID}_f${ffpgas_t} 20 >>h3_f${ID}.di">>h3_f${ID}.bat     


		 else
		   echo "echo wrgtlanes ${fquads_t} pin_sds_chn?_rxp_xi_sv${fseqs_t}_f${ffpgas_t}_f${ID}  >>h3_f${ID}.di">>h3_f${ID}.bat  
           echo "echo wrgtlanes 1${fquads_t} pin_sds_chn?_txp_xo_sv${fseqs_t}_f${ID}_f${ffpgas_t} >>h3_f${ID}.di">>h3_f${ID}.bat     
         fi
		else
         
		 if [[ ${ID} -eq 7 ]] ; then
               
           #reverse it
		   echo "echo wrgtlanes ${fquads_t} pin_sds_chn?_rxp_xi_sv${fseqs_t}_f${ffpgas_t}_f${ID} 30 >>h3_f${ID}.di">>h3_f${ID}.bat  
           echo "echo wrgtlanes 1${fquads_t} pin_sds_chn?_txp_xo_sv${fseqs_t}_f${ID}_f${ffpgas_t} 30 >>h3_f${ID}.di">>h3_f${ID}.bat     
         
		   echo "echo wrgtlanes ${fquads_t} pin_sds_chn?_rxp_xi_sv${fseqs_t}_f${ffpgas_t2}_f${ID} 31 >>h3_f${ID}.di">>h3_f${ID}.bat  
           echo "echo wrgtlanes 1${fquads_t} pin_sds_chn?_txp_xo_sv${fseqs_t}_f${ID}_f${ffpgas_t2} 31 >>h3_f${ID}.di">>h3_f${ID}.bat     

		 else

		   echo "echo wrgtlanes ${fquads_t} pin_sds_chn?_rxp_xi_sv${fseqs_t}_f${ffpgas_t}_f${ID} 20 >>h3_f${ID}.di">>h3_f${ID}.bat  
           echo "echo wrgtlanes 1${fquads_t} pin_sds_chn?_txp_xo_sv${fseqs_t}_f${ID}_f${ffpgas_t} 20 >>h3_f${ID}.di">>h3_f${ID}.bat     
         
		   echo "echo wrgtlanes ${fquads_t} pin_sds_chn?_rxp_xi_sv${fseqs_t}_f${ffpgas_t2}_f${ID} 21 >>h3_f${ID}.di">>h3_f${ID}.bat  
           echo "echo wrgtlanes 1${fquads_t} pin_sds_chn?_txp_xo_sv${fseqs_t}_f${ID}_f${ffpgas_t2} 21 >>h3_f${ID}.di">>h3_f${ID}.bat     
         fi


		fi
  
	    




	
	done
    

    #daughter card info:
        #FPGA7 J8 has a GPIM card:
		 if [[ ${ID} -eq 7 ]] ; then
		      echo "echo wrnote #-FPGA7-J8-has-a-GPIM-card         >>h3_f${ID}.di">>h3_f${ID}.bat
              echo "echo jimpt gpim_h3.txt 1 >>h3_f${ID}.di   ">>h3_f${ID}.bat
			  echo "echo jimpt j8_ls.txt 2 >>h3_f${ID}.di   ">>h3_f${ID}.bat
			  echo "echo insert 2 1 0 LVCMOS18 >>h3_f${ID}.di   ">>h3_f${ID}.bat
		 fi

		#FPGA20 J7 has a SFP+ card:
		 if [[ ${ID} -eq 20 ]] ; then
              echo "echo wrnote #-FPGA20-J7-has-a-SFP+-card         >>h3_f${ID}.di">>h3_f${ID}.bat
              echo "echo jimpt sfp_h3.txt 1 >>h3_f${ID}.di   ">>h3_f${ID}.bat
			  echo "echo jimpt j7_ls.txt 2 >>h3_f${ID}.di   ">>h3_f${ID}.bat
			  echo "echo insert 2 1 0 LVCMOS18 >>h3_f${ID}.di   ">>h3_f${ID}.bat





		 fi


    # 
	echo "echo close >>h3_f${ID}.di   ">>h3_f${ID}.bat   
	echo "type h3_f${ID}.di           ">>h3_f${ID}.bat   
	echo "test procs h3_f${ID}.di     ">>h3_f${ID}.bat      
	echo "::                          ">>h3_f${ID}.bat   
    echo "                            ">>h3_f${ID}.bat   
    echo "                            ">>h3_f${ID}.bat 









done
```





