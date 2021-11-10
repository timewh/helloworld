## s2c test tool gennerate xdc readme

## wrgtclk
### example: wrgtclk 1225 pre_name pos_name
    you will get the output:

    set_property PACKAGE_PIN AH9 [get_ports {pre_name_clkn_pos_name}]
    set_property PACKAGE_PIN AH10 [get_ports {pre_name_clkp_pos_name}]
    
    wrgtck --- write gtclk xdc to g_fp![219:232] or[1219:1232]

## wrgtlanes
### ex: wrgtlanes 224 pre_name?pos_name
    you will get the output:
    
    set_property PACKAGE_PIN AL3 [get_ports {pre_nmae0pos_name}]
    set_property PACKAGE_PIN AL4 [get_ports {pre_nmae0pos_name}]
    set_property PACKAGE_PIN AK1 [get_ports {pre_nmae1pos_name}]
    set_property PACKAGE_PIN AK2 [get_ports {pre_nmae1pos_name}]
    set_property PACKAGE_PIN AJ3 [get_ports {pre_nmae2pos_name}]
    set_property PACKAGE_PIN AJ4 [get_ports {pre_nmae2pos_name}]
    set_property PACKAGE_PIN AH1 [get_ports {pre_nmae3pos_name}]
    set_property PACKAGE_PIN AH2 [get_ports {pre_nmae3pos_name}]
    
    224 is represent rx; 1224 is represent tx;2224 is represent inverse rx;3224 represent reverse tx.
    "?" represent 0,1,2,3
    the "rxp" will autoly infer the "rxn" signal.
    
    wrgtlanes --- write gtlanes xdc to g_fp!pram1: [219:232]=RX or[1219:1232]=TX
                 pram2:=netname_p(n is auto) name3=suffix [option or 0 1 2 3 =single lane]
    
    
    ![image](https://user-images.githubusercontent.com/35107934/141075447-9ae2722d-f5cf-4ce0-81f7-646002c2bda6.png)

    
## wrgrst [num] [netname]
 if num > 10  represent vuls440,else represent lx.
 --- write grstn xdc to g_fp![1:4]
 
## wrnote 
 --- write a line comment xdc to g_fp!if no comment or only a blank line.

## wrgck [num] [pre_name] [pos_name]
   between the pre_name and pos_name is "p/n".
   start from 1,if the num > 100, represent the vuls440,else is lx.
--- write gclk xdc to g_fp![1:12]




## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/timewh/helloworld/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/timewh/helloworld/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
