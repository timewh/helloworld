# test tool

## s2c test tool gennerate xdc readme

## (1) wrgtclk

```javascript
example: wrgtclk 1225 pre_name pos_name   
you will get the output:
```

```javascript
    set_property PACKAGE_PIN AH9 [get_ports {pre_name_clkn_pos_name}]
    set_property PACKAGE_PIN AH10 [get_ports {pre_name_clkp_pos_name}]
```

```javascript
wrgtck --- write gtclk xdc to g_fp![219:232] or[1219:1232]
            219 - represent use gtrefclk0    
           1219 - represent use gtrefclk1
```

## (2) wrgtlanes

```javascript
ex: wrgtlanes 224 pre_name?pos_name [0/1/2/3/20/21/30/31]    
you will get the output:
```

```javascript
    set_property PACKAGE_PIN AL3 [get_ports {pre_nmae0pos_name}]
    set_property PACKAGE_PIN AL4 [get_ports {pre_nmae0pos_name}]
    set_property PACKAGE_PIN AK1 [get_ports {pre_nmae1pos_name}]
    set_property PACKAGE_PIN AK2 [get_ports {pre_nmae1pos_name}]
    set_property PACKAGE_PIN AJ3 [get_ports {pre_nmae2pos_name}]
    set_property PACKAGE_PIN AJ4 [get_ports {pre_nmae2pos_name}]
    set_property PACKAGE_PIN AH1 [get_ports {pre_nmae3pos_name}]
    set_property PACKAGE_PIN AH2 [get_ports {pre_nmae3pos_name}]
```

```javascript
wrgtlanes     
--- write gtlanes xdc to g_fp!    
    param1: [219:232]=RX or[1219:1232]=TX
            224 is represent rx;     
            1224 is represent tx;   
            2224 is represent reverse(pin loc 0123=>3210) rx;    
            3224 represent reverse(pin loc 0123=>3210) tx.   
            you can also use the name:
 ```           
> char ls_jarray_map[][10]={"J4","J3","J2","J1+J8","JX2-M1","JX2-M2","JX1-M1","JX1-M2","MDM","J7","J6","J5"};    
> //the above map is 11->0:232->219    
> unsigned int vuquad[12]={232,231,230,229,227,226,225,224,222,221,220,219};   
```javascript           
            when use the name 'J?' , you need to add another param more ,like : T/T!/R/R!
```             
> t1 =jname2quad(ObName1);    
> //this place need to add another param more! [RX/TX/!(PM_MSAS)]   
> t = t + InStrSingGet(OperateS+t,ObName1);   
> if(ObName1[0] == 'T')  t1+=1000;   
> //when orient the PM_MSAS card we need and the '!' param!    
> if(strseek(ObName1,'!',4))   
>   {   
>       easy_xdc_namespc::printf("RV is used in this QUAD!\n");   
>       t1+=2000;   
>   }   

```javascript
    param2: netname_p(n is auto) 
    "?" represent 0,1,2,3 position.
    程式1 _p => _n  or _p_ => _n_
    程式2 xp_ => xn_ or xp[ => xn[ and add a ']' 
    
    
    param3: suffix  or [option or 0 1 2 3 20 21 30 31 =single lane]   
            20:lane0,lane1   
            21:lane2,lane3   
            30:reverse of 20 , lane0 <-> lane1   
            31:reverse of 31 , lane2 <-> lane3   
```

## (3) wrgrst

```javascript
 wrgrst [num] [netname]      
 write grstn xdc to g_fp![1:4]     
 if num start from  11  represent vuls440,else represent lx.      
```    


## (4) wrgck

```javascript
   wrgck [num] [pre_name] [pos_name]       
   write gclk xdc to g_fp![1:12]        
   between the pre_name and pos_name is "p/n".    
   start from 1,if the num start from 101, represent the vuls440,else is lx.    
``` 
 
## (5) insert


```javascript
 --- insert one dcard to jpos after they are loaded to g_fp!:
pram1=connetor pram2=dcard |1-64
param3: if not use please give '0' or omit,
        if '1' ->represent debug mode,it will print the debug info.
        if '5' ->used to represent the merge mode to generate a new daught card info.normally for ddr4.
param4：example “LVCMOS18”,used to define the voltage type!
        if not used can omit!
```

examp: we insert one card on VULS j8 :

```javascript
open gpim_h3.xdc
jimpt gpim_h3.txt 1
jimpt j8_ls.txt 2
insert 2 1 0 LVCOMS18
close
```

in the gpim_h3.txt :

```javascript
H14 SPI1_CS
H11 SPI1_RESET
G14 SPI1_SCK
H13 SPI1_SI
G17 SPI1_SO
H16 SPI1_WP
```

int the j8_ls.txt ：

```javascript
C3 BP10 IO_L20N_T3L_N3_AD1N_60 Bank60
C2 BP11 IO_L20P_T3L_N2_AD1P_60 Bank60
C7 BL13 IO_L17N_T2U_N9_AD10N_60 Bank60
C6 BK13 IO_L17P_T2U_N8_AD10P_60 Bank60
C11 BP20 IO_L2N_T0L_N3_60 Bank60
C10 BP21 IO_L2P_T0L_N2_60 Bank60
D2 BP9 IO_L21N_T3L_N5_AD8N_60 Bank60
D1 BN9 IO_L21P_T3L_N4_AD8P_60 Bank60
...

```

you will get the out file gpim_h3.xdc:

```javascript
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



## (6) DDR4 Match

### (a) insert ddr4 card

example:

```javascript
   open itcd.xdc
   jimpt p-pm-ddr4.txt 1
   jimpt j7_ls.txt 2
   insert 2 1 5
   close
```



  首先准备格式化txt文件：    
    1，连接器txt文件：格式要求：C11	BG15	IO_L6N_T0U_N11_AD6N_63	Bank63

```
       每一行都必须满足上面的格式，其中第一列是接插件位置索引，第二列位FPGA位置索引，
       一般对应不同平台已经准备好了标准化的文件在s2c目录下
```

​    2，子卡txt文件：格式要求： C2 DDR4_DM4 

```
       每一行都必须满足上面的格式，
       其中第一列是接插件位置索引，
       第二列位net的具体名字含义会直接输出到xdc文件
       其次可以导入的地址空间范围位1-64，执行insert命令时，第一个参数为connector,第二个为子卡，
       第三个参数指定输出格式0-normal 1-debug 5-card and connector merge 
       第四个参数为电平标准（LVCMOS18/），也可以不输入
       最终输出的结果位于itcd.xdc文件中！
```

### (b) rmatxdc

一般用于ddr4约束(使用之前必须对输入和查找之间做语义替换)：
比如:(源addr4)=>(目的a4)，匹配的原则是按照

+ 单词匹配，并且被匹配的单词出现的次数越高则权重越高，同权重的匹配结果，则取最短的作为最佳输出

+ 数字可移位等价(语义替换的一种/c或n加数字的模式)：ck_c[0]/CKP0 => ckc0/ck0c/ck0_c/ck_0c/ck_c0 
  语义替换的原则一般在目的匹配值为标准模板的情况下，将非统一输入向目的模板做语义匹配！
+ 增加关键字匹配权重
  //dqs dm odt adr ck cke cs ba bg act reset dq

```javascript
param1: the daughtcard file
param2: the target.xdc
param3: the search index of key words in the target.xdc
param4: the target index need to update in the target.xdc
```

after the cmd run , it will gennerate a same name file of param2,int the output dir!    

```javascript
rmatxdc ddr4.txt ddr4_example.xdc 5 3
rmatxdc ddr4_j7ls.txt ddr4_example2.xdc 6 3
rmatxdc itcd.xdc ddr4_example2.xdc 6 3
```


### (c) rmatch
```javascript
jimpt ddr4.txt 1 
//note: '1 1' of 'rmatch 1 1' is defualt value!do not care!
//first 1: represent 1-64 mem buffer;
//second 1: represent the search match index of the mem buffer.
rmatch 1 1 "c0_ddr4_dq[1]" //   {c0_ddr4_dq[36]}]
rmatch 1 1 {DDR0_ADDR[4]}]
rmatch 1 1 {c0_ddr4_adr[4]]} 
rmatch 1 1 {DDR0_BA[0]}]
rmatch 1 1 DDR0_CKN0   
rmatch 1 1 c0_ddr4_ck_c[0]    //=>DDR4_CK0_C DDR0_CKN0   
//c0=0_c  // the positive edge of CK_t and negative edge of CK_c
rmatch 1 1 {c0_ddr4_cke[0]]}  //DDR4_CKE0 DDR0_CKE0
rmatch 1 1 {c0_ddr4_cs_n[0]]} //DDR4_CS0_N  DDR0_CS0
//{DDR0_DM_P[0]} {c0_ddr4_dm_dbi_n[0]]}  ddr4_dm0
//{DDR0_DQSP[0]}] {DDR0_DQSB[0]}] "c0_ddr4_dqs_t[0]" "c0_ddr4_dqs_c[8]"  DDR4_DQS6_T
```


![image](https://user-images.githubusercontent.com/35107934/142165287-513b582f-bf58-42d7-95ab-f7e8533285d2.png)


## (7) wrnote

 write a line comment xdc to g_fp!    
 if no comment or only a blank line.        



## (8) example

![image](https://user-images.githubusercontent.com/35107934/142143964-90f7a9b4-f9f2-4204-adc7-468d52e595bc.png)

## Welcome to GitHub Pages

[My Blog](https://www.cnblogs.com/time93/)
