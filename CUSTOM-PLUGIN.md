
## htdots => wp-Content => plugins => Cusome-plugin-Folder => custom-plugin.php

<img width="1160" height="570" alt="image" src="https://github.com/user-attachments/assets/798d59bb-47f7-44aa-9d50-2094f8ae9b30" />
<img width="725" height="78" alt="image" src="https://github.com/user-attachments/assets/807f9f1f-11cb-47df-8200-2f03770ebc1e" />

- SUB SA IMPORTANT HA KA Plugin Name ki spell or likhana sehi sa ha warna show nahi hu ga plugin,baki pa galti kar sakhata hu,
- How to add Menu in Custom plugin.
- Menu ka matlab side bar pa woh plugin show hu Active karna ka bad ,or jab Deactivate karo to remove hu jaya.

## Go To https://developer.wordpress.org/ => yaha ap ko Menu add karna ka Function mela ga.
- yeh function PHP ka NAHI ha yeh wordPress ka Function ha.
- WordPress pa kesi bhi Function ko Run karna ka lia ya Customize karna ka lia hama Triger Point chahiya huta ha like ,Hooks ,Action & Filter
- add_menu_page Function ka kuch parameter Required ha or kuch optional value ha yani ka default value di hua ha.
  <img width="882" height="160" alt="image" src="https://github.com/user-attachments/assets/ba4ff3a8-7994-4b18-805f-3834213fed28" />

```
add_menu_page( string $page_title, string $menu_title, string $capability, string $menu_slug, callable $callback, string $icon_url, int|float $position = null ): string
```
# Control + U (View Source Page)

## string $page_title
<img width="982" height="297" alt="image" src="https://github.com/user-attachments/assets/4a594984-8eae-4ab3-abae-4d86ee35bffd" />

## string $menu_title
<img width="1019" height="598" alt="image" src="https://github.com/user-attachments/assets/41029da9-c591-46b2-a6d3-1f50ecc30512" />

## string $capability 
### User Role (manage_options) => Admin Full Control

## string $menu_slug
<img width="903" height="580" alt="image" src="https://github.com/user-attachments/assets/1e86dedd-a101-48ac-b8be-0b017436b152" />

## callable $callback (Function Logic)
<img width="568" height="158" alt="image" src="https://github.com/user-attachments/assets/f290834a-7525-4fe9-b8ae-4d5e6621b358" />

## string $icon_url
<img width="933" height="333" alt="image" src="https://github.com/user-attachments/assets/9226d0bf-6512-4798-b442-cda73a80eee2" />
<img width="1344" height="565" alt="image" src="https://github.com/user-attachments/assets/fe32d476-b3f9-42cd-a8b5-938ed2fbb0b2" />

## int|float $position = null

<img width="457" height="432" alt="image" src="https://github.com/user-attachments/assets/08c81ae2-f18b-49ef-b55b-65c8f5051ad3" />

<img width="1047" height="431" alt="image" src="https://github.com/user-attachments/assets/bf8aea72-f32c-4839-8656-9fcfc8f77cc3" />

### CallBack Function ka name hamesha ( _ )sa rakho na - na kuch or
#### echo = console.log() & Print""
<img width="1206" height="594" alt="image" src="https://github.com/user-attachments/assets/e62b5fcd-8bdc-427b-84a2-e95bfde63150" />

# SUB MENU 
## How to Add Sub Menu in Custom Plugin ⛺.
<img width="645" height="439" alt="image" src="https://github.com/user-attachments/assets/e1fab730-1a53-40da-9af6-a2c838da2118" />
<img width="754" height="302" alt="image" src="https://github.com/user-attachments/assets/06f9b96f-06f4-48ef-b38d-06756dd7ff31" />
<img width="1065" height="463" alt="image" src="https://github.com/user-attachments/assets/35c06400-1e12-449d-b5b7-bf657e1a4fe2" />
## Add Sub Menu
<img width="1325" height="398" alt="image" src="https://github.com/user-attachments/assets/eef8e43b-d9ec-4ade-b34b-451714dbea63" />
<img width="1054" height="156" alt="image" src="https://github.com/user-attachments/assets/c3ee30af-043c-424b-8c5a-3aadbc680e6a" />

### Sub_menu_page ka under Parents Slug ka name dalna ha
- Jab hum Parent Menu pa click karta ha to woh Sub Menu pa hi jata ha to is lia hum 1 function hi bana ga jo sub menu ka hi function hu ga
- Jab hu Post pa click karta ha to us ka Sub menu open huta ha jis ka matlab Parent ka Slub or Fist SubMenu ka slug same huta ha
<img width="1062" height="391" alt="image" src="https://github.com/user-attachments/assets/b8626f22-13d0-4447-a406-1dda13dbeae6" />
<img width="987" height="433" alt="image" src="https://github.com/user-attachments/assets/338aa67f-451e-4727-b8d5-0cc928e5295b" />
<img width="628" height="414" alt="image" src="https://github.com/user-attachments/assets/b265d861-bec7-4cd2-b4c2-e217a056d821" />


# Menus and Sub-Menus Layouts 🗾♨🗾
## Layout Mens Folder Structure 
- Dekho hum Sub_Menu page ha us ka content Parent Manue pa rakha to ek hi file pa bohat ziyada content hu jaya ga is lia hum layout banata ha.

## Wp-Content => Plugin => Custom Folder => Create new Folder (ABC Name Kuch bhi)(Pages) => Create File (add-employee.php)
<img width="388" height="355" alt="image" src="https://github.com/user-attachments/assets/3ca60491-9860-48c6-bc95-ffc560a7ba26" />
## Yeh 2 Sub Menu Function ha is ki logic hum ab layout wali files pa likha ga
<img width="630" height="354" alt="image" src="https://github.com/user-attachments/assets/0dfb26be-6910-4acb-92ac-50d61fac593b" />

## Ab jo pages name ka Folder ka under jo hum na 2 file banai ha us ka path kaisa da 
<img width="525" height="60" alt="image" src="https://github.com/user-attachments/assets/e03711b4-1102-4324-a995-2351c7b4257b" />

<img width="668" height="35" alt="image" src="https://github.com/user-attachments/assets/d1cefc10-8872-4f3b-9b6f-8c6cec4de2b9" />
### Ek Constant PHP ka varible banao define() sa us ka under path save karo
```
define("EMS_PLUGIN_PATH",plugin_dir_path(__FILE__));
```
<img width="892" height="237" alt="image" src="https://github.com/user-attachments/assets/7e3966a1-f742-4785-8741-d5c96327d427" />
### yeh alternate ha varible decrle karna ka $path varible sa
<img width="803" height="186" alt="image" src="https://github.com/user-attachments/assets/53e24b68-11c3-400a-85eb-17e6e2174f5f" />

<img width="662" height="377" alt="image" src="https://github.com/user-attachments/assets/7ebd5e87-0b04-4558-baa1-dfb4c4041e9a" />
### . Dot na Contactenate ha jo javasript pa + + sa huta ha
<img width="1010" height="472" alt="image" src="https://github.com/user-attachments/assets/6ab6aca3-8bdf-4c89-8858-8dca550221e8" />
<img width="890" height="474" alt="image" src="https://github.com/user-attachments/assets/840683ed-0cd8-43ee-892f-29c56883e148" />
## W3 School 
- W3 School sa hum bootstrap pa form ka code bhi la sakhta h

<img width="1189" height="616" alt="image" src="https://github.com/user-attachments/assets/94f3b24d-c8ae-4616-aa93-47404bcb5e5b" />
<img width="1214" height="640" alt="image" src="https://github.com/user-attachments/assets/dfb089e3-7c2f-48c4-a089-ae845059d30b" />


# Settings of Layout (Add, List) 🕸

# 🔥 WordPress Plugin Structure (Explained)
```
my-plugin/
│
├── my-plugin.php          
│   → Main entry file (plugin start karta hai, hooks + includes handle karta hai)
│
├── uninstall.php          
│   → Plugin delete hone par cleanup (DB, options delete)
│
├── readme.txt             
│   → Plugin description, version, usage (WordPress.org ke liye)
│
├── includes/              
│   → Core logic (plugin ka brain)
│   │
│   ├── class-loader.php   
│   │   → Saari files/classes ko load/manage karta hai (advanced structure)
│   │
│   ├── class-init.php     
│   │   → Plugin initialize karta hai (hooks register, main flow control)
│   │
│   └── helpers.php        
│       → Chhote reusable functions (utility helpers)
│
├── admin/                 
│   → Sirf admin panel (dashboard) ke liye code
│   │
│   ├── class-admin-menu.php  
│   │   → Admin menu create karta hai (add_menu_page, submenu)
│   │
│   └── class-admin-page.php  
│       → Admin page ka UI (HTML output, forms, settings)
│
├── public/                
│   → Frontend (website side) ke liye code
│   │
│   └── class-public.php   
│       → Frontend display, CSS/JS load, shortcodes etc.
│
├── assets/                
│   → Static files (design + scripts)
│   │
│   ├── css/               
│   │   → Styling files (admin + frontend)
│   │
│   ├── js/                
│   │   → JavaScript files (AJAX, interactivity)
│   │
│   └── images/            
│       → Icons, images
```
# ⚡ Short Summary (jaldi revise karne ke liye)
- my-plugin.php → start point
- includes/ → logic
- admin/ → dashboard
- public/ → frontend
- assets/ → CSS/JS
- uninstall.php → cleanup




