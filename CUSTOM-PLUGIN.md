
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

## string $icon_url
<img width="933" height="333" alt="image" src="https://github.com/user-attachments/assets/9226d0bf-6512-4798-b442-cda73a80eee2" />
<img width="1344" height="565" alt="image" src="https://github.com/user-attachments/assets/fe32d476-b3f9-42cd-a8b5-938ed2fbb0b2" />

## int|float $position = null

<img width="457" height="432" alt="image" src="https://github.com/user-attachments/assets/08c81ae2-f18b-49ef-b55b-65c8f5051ad3" />

<img width="1047" height="431" alt="image" src="https://github.com/user-attachments/assets/bf8aea72-f32c-4839-8656-9fcfc8f77cc3" />

### CallBack Function ka name hamesha ( _ )sa rakho na - na kuch or
#### echo = console.log() & Print""
<img width="1206" height="594" alt="image" src="https://github.com/user-attachments/assets/e62b5fcd-8bdc-427b-84a2-e95bfde63150" />

