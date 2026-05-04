
## htdots => wp-Content => plugins => Cusome-plugin-Folder => custom-plugin.php

<img width="1160" height="570" alt="image" src="https://github.com/user-attachments/assets/798d59bb-47f7-44aa-9d50-2094f8ae9b30" />
<img width="725" height="78" alt="image" src="https://github.com/user-attachments/assets/807f9f1f-11cb-47df-8200-2f03770ebc1e" />

- SUB SA IMPORTANT HA KA Plugin Name ki spell or likhana sehi sa ha warna show nahi hu ga plugin,baki pa galti kar sakhata hu,
- How to add Menu in Custom plugin.
- Menu ka matlab side bar pa woh plugin show hu Active karna ka bad ,or jab Deactivate karo to remove hu jaya.

## Go To https://developer.wordpress.org/ => yaha ap ko Menu add karna ka Function mela ga.
- yeh function PHP ka NAHI ha yeh wordPress ka Function ha.
- WordPress pa kesi bhi Function ko Run karna ka lia ya Customize karna ka lia hama Triger Point chahiya huta ha like ,Hooks ,Action & Filter
  <img width="882" height="160" alt="image" src="https://github.com/user-attachments/assets/ba4ff3a8-7994-4b18-805f-3834213fed28" />

```
add_menu_page( string $page_title, string $menu_title, string $capability, string $menu_slug, callable $callback, string $icon_url, int|float $position = null ): string
```
