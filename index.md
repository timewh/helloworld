## s2c test tool gennerate xdc readme

## wrgtclk
    example: wrgtclk 1225 pre_name pos_name   
    you will get the output:
```
    set_property PACKAGE_PIN AH9 [get_ports {pre_name_clkn_pos_name}]
    set_property PACKAGE_PIN AH10 [get_ports {pre_name_clkp_pos_name}]
```    
    wrgtck --- write gtclk xdc to g_fp![219:232] or[1219:1232]

## wrgtlanes
    ex: wrgtlanes 224 pre_name?pos_name [0/1/2/3/20/21/30/31]    
    you will get the output:
```    
    set_property PACKAGE_PIN AL3 [get_ports {pre_nmae0pos_name}]
    set_property PACKAGE_PIN AL4 [get_ports {pre_nmae0pos_name}]
    set_property PACKAGE_PIN AK1 [get_ports {pre_nmae1pos_name}]
    set_property PACKAGE_PIN AK2 [get_ports {pre_nmae1pos_name}]
    set_property PACKAGE_PIN AJ3 [get_ports {pre_nmae2pos_name}]
    set_property PACKAGE_PIN AJ4 [get_ports {pre_nmae2pos_name}]
    set_property PACKAGE_PIN AH1 [get_ports {pre_nmae3pos_name}]
    set_property PACKAGE_PIN AH2 [get_ports {pre_nmae3pos_name}]
```   
     224 is represent rx;     
    1224 is represent tx;   
    2224 is represent reverse(pin loc 0123=>3210) rx;    
    3224 represent reverse(pin loc 0123=>3210) tx.   
    "?" represent 0,1,2,3    
    the "rxp" will autoly infer the "rxn" signal.
    
    wrgtlanes --- write gtlanes xdc to g_fp!pram1: [219:232]=RX or[1219:1232]=TX    
                 pram2:=netname_p(n is auto) name3=suffix [option or 0 1 2 3 =single lane]   
    20:lane0,lane1   
    21:lane2,lane3   
    30:reverse of 20 , lane0 <-> lane1   
    31:reverse of 31 , lane2 <-> lane3   
    

![image](https://user-images.githubusercontent.com/35107934/141075447-9ae2722d-f5cf-4ce0-81f7-646002c2bda6.png)

    
## wrgrst 
wrgrst [num] [netname]    
 if num > 10  represent vuls440,else represent lx.    
 --- write grstn xdc to g_fp![1:4]
 
## wrnote 
 --- write a line comment xdc to g_fp!if no comment or only a blank line.

## wrgck
   wrgck [num] [pre_name] [pos_name]    
   between the pre_name and pos_name is "p/n".    
   start from 1,if the num > 100, represent the vuls440,else is lx.    
--- write gclk xdc to g_fp![1:12]    

## insert
 --- insert one dcard to jpos after they are loaded to g_fp!:    
pram1=connetor pram2=dcard |1-64    
param3: if not use please give '0' or omit,    
        if '1' ->represent debug mode,it will print the debug info.    
        if '5' ->used to represent the merge mode to generate a new daught card info.normally for ddr4.    
param4：example “LVCMOS18”,used to define the voltage type!    
        if not used can omit!    

examp: we insert one card on VULS j8 :    
```
open gpim_h3.xdc
jimpt gpim_h3.txt 1
jimpt j8_ls.txt 2
insert 2 1 0 LVCOMS18
close
```
in the gpim_h3.txt :   
```
H14	SPI1_CS
H11	SPI1_RESET
G14	SPI1_SCK
H13	SPI1_SI
G17	SPI1_SO
H16	SPI1_WP
```
int the j8_ls.txt ：   
```
C3	BP10	IO_L20N_T3L_N3_AD1N_60	Bank60
C2	BP11	IO_L20P_T3L_N2_AD1P_60	Bank60
C7	BL13	IO_L17N_T2U_N9_AD10N_60	Bank60
C6	BK13	IO_L17P_T2U_N8_AD10P_60	Bank60
C11	BP20	IO_L2N_T0L_N3_60	Bank60
C10	BP21	IO_L2P_T0L_N2_60	Bank60
D2	BP9	IO_L21N_T3L_N5_AD8N_60	Bank60
D1	BN9	IO_L21P_T3L_N4_AD8P_60	Bank60
...

```
you will get the out file gpim_h3.xdc:
```
#-----------------------------
set_property PACKAGE_PIN BK25 [get_ports {SPI1_CS}]
set_property IOSTANDARD LVCMOS18 [get_ports {SPI1_CS}]
set_property PACKAGE_PIN BL23 [get_ports {SPI1_RESET}]
set_property IOSTANDARD LVCMOS18 [get_ports {SPI1_RESET}]
set_property PACKAGE_PIN BK27 [get_ports {SPI1_SCK}]
set_property IOSTANDARD LVCMOS18 [get_ports {SPI1_SCK}]
set_property PACKAGE_PIN BK26 [get_ports {SPI1_SI}]
set_property IOSTANDARD LVCMOS18 [get_ports {SPI1_SI}]
set_property PACKAGE_PIN BP29 [get_ports {SPI1_SO}]
set_property IOSTANDARD LVCMOS18 [get_ports {SPI1_SO}]
set_property PACKAGE_PIN BM29 [get_ports {SPI1_WP}]
set_property IOSTANDARD LVCMOS18 [get_ports {SPI1_WP}]
#------------end----------------
```






![image](https://user-images.githubusercontent.com/35107934/142143964-90f7a9b4-f9f2-4204-adc7-468d52e595bc.png)




## Welcome to GitHub Pages
[My Blog](https://www.cnblogs.com/time93/)



