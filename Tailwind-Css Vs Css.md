# CSS vs Tailwind CSS Complete Reference

## Layout & Display

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `flex` | `display: flex` | Container ko flexbox banata hai | `<div class="flex">...</div>` |
| `grid` | `display: grid` | Container ko grid layout banata hai | `<div class="grid">Grid</div>` |
| `block` | `display: block` | Element ko block element banata hai | `<div class="block">Block</div>` |
| `inline-block` | `display: inline-block` | Inline block element banata hai | `<span class="inline-block">Inline Block</span>` |
| `hidden` | `display: none` | Element ko completely hide karta hai | `<div class="hidden">Hidden</div>` |
| `invisible` | `visibility: hidden` | Element invisible karta hai, space retain karta hai | `<div class="invisible">Invisible</div>` |

## Flexbox

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `flex-col` | `flex-direction: column` | Elements vertical arrange karta hai | `<div class="flex flex-col">Vertical</div>` |
| `flex-row` | `flex-direction: row` | Elements horizontal arrange karta hai (default) | `<div class="flex flex-row">Horizontal</div>` |
| `justify-center` | `justify-content: center` | Horizontal center align karta hai | `<div class="flex justify-center">Center</div>` |
| `justify-between` | `justify-content: space-between` | Elements ke beech equal space deta hai | `<div class="flex justify-between">Space Between</div>` |
| `items-center` | `align-items: center` | Vertical center align karta hai | `<div class="flex items-center">Vert Center</div>` |
| `items-start` | `align-items: flex-start` | Top align karta hai | `<div class="flex items-start">Top Align</div>` |

## Spacing

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `m-4` | `margin: 1rem` | 16px margin all sides | `<div class="m-4">Margin All</div>` |
| `mx-4` | `margin-left: 1rem; margin-right: 1rem` | Horizontal margin | `<div class="mx-4">Margin X</div>` |
| `my-4` | `margin-top: 1rem; margin-bottom: 1rem` | Vertical margin | `<div class="my-4">Margin Y</div>` |
| `mt-4` | `margin-top: 1rem` | Top margin | `<div class="mt-4">Margin Top</div>` |
| `p-4` | `padding: 1rem` | 16px padding all sides | `<div class="p-4">Padding All</div>` |
| `px-4` | `padding-left: 1rem; padding-right: 1rem` | Horizontal padding | `<div class="px-4">Padding X</div>` |
| `py-4` | `padding-top: 1rem; padding-bottom: 1rem` | Vertical padding | `<div class="py-4">Padding Y</div>` |
| `mx-auto` | `margin: 0 auto` | Element ko horizontally center karta hai | `<div class="mx-auto w-32">Centered</div>` |
| `space-x-4` | `margin-right: 1rem` (on children) | Children ke beech horizontal gap | `<div class="flex space-x-4"><div>A</div><div>B</div></div>` |

## Typography

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `text-center` | `text-align: center` | Text ko center align karta hai | `<p class="text-center">Centered</p>` |
| `text-left` | `text-align: left` | Text ko left align karta hai | `<p class="text-left">Left Align</p>` |
| `text-right` | `text-align: right` | Text ko right align karta hai | `<p class="text-right">Right Align</p>` |
| `font-bold` | `font-weight: 700` | Text ko bold banata hai | `<h1 class="font-bold">Bold Text</h1>` |
| `font-medium` | `font-weight: 500` | Medium font weight | `<p class="font-medium">Medium</p>` |
| `font-normal` | `font-weight: 400` | Normal font weight | `<p class="font-normal">Normal</p>` |
| `text-xl` | `font-size: 1.5rem` | Font size 24px (extra large) | `<p class="text-xl">Large Text</p>` |
| `text-lg` | `font-size: 1.125rem` | Font size 18px (large) | `<p class="text-lg">Large</p>` |
| `text-base` | `font-size: 1rem` | Font size 16px (base) | `<p class="text-base">Base Size</p>` |
| `text-sm` | `font-size: 0.875rem` | Font size 14px (small) | `<p class="text-sm">Small Text</p>` |
| `leading-normal` | `line-height: 1.5` | Normal line height (150%) | `<p class="leading-normal">Normal Lines</p>` |
| `leading-tight` | `line-height: 1.25` | Tight line height (125%) | `<p class="leading-tight">Tight Lines</p>` |
| `uppercase` | `text-transform: uppercase` | Text ko uppercase letters mein convert karta hai | `<p class="uppercase">UPPERCASE</p>` |
| `lowercase` | `text-transform: lowercase` | Text ko lowercase letters mein convert karta hai | `<p class="lowercase">lowercase</p>` |
| `capitalize` | `text-transform: capitalize` | Har word ka first letter capitalize karta hai | `<p class="capitalize">Capitalize Text</p>` |
| `underline` | `text-decoration: underline` | Text ko underline karta hai | `<a class="underline">Link</a>` |
| `no-underline` | `text-decoration: none` | Underline remove karta hai | `<a class="no-underline">No Underline</a>` |
| `italic` | `font-style: italic` | Text ko italic banata hai | `<p class="italic">Italic Text</p>` |

## Colors & Background

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `bg-blue-500` | `background-color: #3b82f6` | Blue background color | `<div class="bg-blue-500">Blue BG</div>` |
| `bg-red-500` | `background-color: #ef4444` | Red background color | `<div class="bg-red-500">Red BG</div>` |
| `bg-gray-100` | `background-color: #f3f4f6` | Light gray background | `<div class="bg-gray-100">Light Gray</div>` |
| `bg-white` | `background-color: #ffffff` | White background | `<div class="bg-white">White</div>` |
| `bg-black` | `background-color: #000000` | Black background | `<div class="bg-black">Black</div>` |
| `text-white` | `color: #ffffff` | White text color | `<p class="text-white">White Text</p>` |
| `text-black` | `color: #000000` | Black text color | `<p class="text-black">Black Text</p>` |
| `text-gray-600` | `color: #4b5563` | Gray text color | `<p class="text-gray-600">Gray Text</p>` |
| `bg-opacity-50` | `opacity: 0.5` | Background ki opacity 50% karta hai | `<div class="bg-blue-500 bg-opacity-50">Semi-transparent</div>` |

## Borders

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `border` | `border: 1px solid #e5e7eb` | 1px light gray border | `<div class="border">Border</div>` |
| `border-2` | `border-width: 2px` | 2px border width | `<div class="border-2">Thick Border</div>` |
| `border-red-500` | `border-color: #ef4444` | Red border color | `<div class="border border-red-500">Red Border</div>` |
| `rounded` | `border-radius: 0.25rem` | Small rounded corners (4px) | `<div class="rounded">Rounded</div>` |
| `rounded-lg` | `border-radius: 0.5rem` | Medium rounded corners (8px) | `<div class="rounded-lg">Large Rounded</div>` |
| `rounded-full` | `border-radius: 9999px` | Perfect circle/oval banata hai | `<div class="rounded-full">Circle</div>` |
| `border-solid` | `border-style: solid` | Solid border style | `<div class="border-solid">Solid Border</div>` |
| `border-dashed` | `border-style: dashed` | Dashed border style | `<div class="border-dashed">Dashed Border</div>` |

## Sizing

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `w-full` | `width: 100%` | Element ki width 100% karta hai | `<div class="w-full">Full Width</div>` |
| `w-1/2` | `width: 50%` | Element ki width 50% karta hai | `<div class="w-1/2">Half Width</div>` |
| `w-64` | `width: 16rem` | Fixed width 256px | `<div class="w-64">Fixed Width</div>` |
| `h-screen` | `height: 100vh` | Element ki height viewport ke equal | `<div class="h-screen">Full Height</div>` |
| `h-full` | `height: 100%` | Element ki height parent ke 100% | `<div class="h-full">Full Height</div>` |
| `min-h-screen` | `min-height: 100vh` | Minimum height viewport ke equal | `<div class="min-h-screen">Min Height</div>` |
| `max-w-md` | `max-width: 28rem` | Maximum width 448px | `<div class="max-w-md">Max Width</div>` |

## Position

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `relative` | `position: relative` | Element ko relative position deta hai | `<div class="relative">Relative</div>` |
| `absolute` | `position: absolute` | Element ko absolute position deta hai | `<div class="absolute">Absolute</div>` |
| `fixed` | `position: fixed` | Element ko fixed position deta hai | `<div class="fixed">Fixed</div>` |
| `sticky` | `position: sticky` | Element ko sticky position deta hai | `<div class="sticky top-0">Sticky</div>` |
| `top-0` | `top: 0px` | Element ko top se 0px par rakhta hai | `<div class="absolute top-0">Top 0</div>` |
| `right-4` | `right: 1rem` | Element ko right se 16px par rakhta hai | `<div class="absolute right-4">Right 4</div>` |
| `z-10` | `z-index: 10` | Element ki stacking order set karta hai | `<div class="z-10">On Top</div>` |
| `z-50` | `z-index: 50` | High z-index for overlays | `<div class="z-50">Highest Layer</div>` |

## Grid

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `grid-cols-3` | `grid-template-columns: repeat(3, 1fr)` | 3 equal width columns banata hai | `<div class="grid grid-cols-3">3 Columns</div>` |
| `grid-cols-2` | `grid-template-columns: repeat(2, 1fr)` | 2 equal width columns | `<div class="grid grid-cols-2">2 Columns</div>` |
| `col-span-2` | `grid-column: span 2` | Element 2 columns occupy karega | `<div class="col-span-2">Span 2 Cols</div>` |
| `gap-4` | `gap: 1rem` | Grid items ke beech 16px gap | `<div class="grid gap-4">With Gap</div>` |
| `gap-x-2` | `column-gap: 0.5rem` | Columns ke beech 8px gap | `<div class="grid gap-x-2">Column Gap</div>` |
| `gap-y-4` | `row-gap: 1rem` | Rows ke beech 16px gap | `<div class="grid gap-y-4">Row Gap</div>` |

## Effects & Transitions

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `shadow` | `box-shadow: 0 1px 3px 0 rgba(0,0,0,0.1)` | Light shadow lagata hai | `<div class="shadow">Shadow</div>` |
| `shadow-lg` | `box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1)` | Large shadow lagata hai | `<div class="shadow-lg">Large Shadow</div>` |
| `opacity-50` | `opacity: 0.5` | Element ko 50% transparent karta hai | `<div class="opacity-50">Semi-transparent</div>` |
| `transition-all` | `transition: all 0.3s ease` | Smooth transition sabhi properties pe | `<div class="transition-all">Transition</div>` |
| `duration-300` | `transition-duration: 300ms` | Transition duration 300ms | `<div class="transition-all duration-300">300ms</div>` |
| `ease-in` | `transition-timing-function: ease-in` | Ease-in transition curve | `<div class="transition-all ease-in">Ease In</div>` |
| `ease-out` | `transition-timing-function: ease-out` | Ease-out transition curve | `<div class="transition-all ease-out">Ease Out</div>` |

## Transform

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `transform` | `transform: ...` | Transform properties ke liye required | `<div class="transform">Transform</div>` |
| `scale-105` | `transform: scale(1.05)` | Element ko 5% zoom karta hai | `<div class="scale-105">Zoomed</div>` |
| `rotate-45` | `transform: rotate(45deg)` | Element ko 45° rotate karta hai | `<div class="rotate-45">Rotated</div>` |
| `translate-x-4` | `transform: translateX(1rem)` | Element ko right shift karta hai 16px | `<div class="translate-x-4">Shifted Right</div>` |
| `-translate-y-2` | `transform: translateY(-0.5rem)` | Element ko up shift karta hai 8px | `<div class="-translate-y-2">Shifted Up</div>` |

## Interactivity

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `hover:bg-gray-200` | `:hover { background: #e5e7eb }` | Hover pe background change | `<button class="hover:bg-gray-200">Hover me</button>` |
| `focus:outline-none` | `:focus { outline: none }` | Focus pe outline remove karta hai | `<input class="focus:outline-none">` |
| `active:scale-95` | `:active { transform: scale(0.95) }` | Click pe thoda shrink karta hai | `<button class="active:scale-95">Click me</button>` |
| `cursor-pointer` | `cursor: pointer` | Mouse cursor ko pointer banata hai | `<div class="cursor-pointer">Clickable</div>` |
| `cursor-not-allowed` | `cursor: not-allowed` | Not allowed cursor dikhata hai | `<button disabled class="cursor-not-allowed">Disabled</button>` |

## Responsive Design

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `sm:text-lg` | `@media (min-width: 640px) { font-size: 1.125rem }` | Small screens pe large text | `<p class="sm:text-lg">Responsive</p>` |
| `md:flex` | `@media (min-width: 768px) { display: flex }` | Medium screens pe flex | `<div class="md:flex">Flex on medium</div>` |
| `lg:hidden` | `@media (min-width: 1024px) { display: none }` | Large screens pe hide | `<div class="lg:hidden">Hide on large</div>` |
| `xl:grid-cols-4` | `@media (min-width: 1280px) { grid-template-columns: repeat(4, 1fr) }` | XL screens pe 4 columns | `<div class="xl:grid-cols-4">4 Cols on XL</div>` |

## Background & Images

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `bg-cover` | `background-size: cover` | Background image ko cover karta hai | `<div class="bg-cover">Cover BG</div>` |
| `bg-contain` | `background-size: contain` | Background image ko contain karta hai | `<div class="bg-contain">Contain BG</div>` |
| `bg-center` | `background-position: center` | Background image ko center karta hai | `<div class="bg-center">Center BG</div>` |
| `bg-no-repeat` | `background-repeat: no-repeat` | Background image repeat nahi karega | `<div class="bg-no-repeat">No Repeat</div>` |
| `bg-gradient-to-r` | `background-image: linear-gradient(to right, ...)` | Horizontal gradient banata hai | `<div class="bg-gradient-to-r from-blue-500 to-purple-500">Gradient</div>` |

## Lists & Tables

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `list-none` | `list-style-type: none` | List ke bullets remove karta hai | `<ul class="list-none">No Bullets</ul>` |
| `list-disc` | `list-style-type: disc` | Disc bullets lagata hai | `<ul class="list-disc">Disc Bullets</ul>` |
| `border-collapse` | `border-collapse: collapse` | Table borders ko collapse karta hai | `<table class="border-collapse">Table</table>` |

## Overflow & Visibility

| Tailwind Class | CSS Property | Definition | Example |
|----------------|--------------|------------|---------|
| `overflow-hidden` | `overflow: hidden` | Overflow content ko hide karta hai | `<div class="overflow-hidden">Hidden Overflow</div>` |
| `overflow-auto` | `overflow: auto` | Overflow pe scrollbar dikhata hai | `<div class="overflow-auto">Auto Scroll</div>` |
| `overflow-scroll` | `overflow: scroll` | Always scrollbar dikhata hai | `<div class="overflow-scroll">Always Scroll</div>` |

# Code Examples

## Example 1: Complete Card Component
```html
<!-- Tailwind -->
<div class="max-w-sm rounded-lg shadow-lg bg-white p-6 m-4">
  <h3 class="text-xl font-bold text-gray-800 mb-2">Card Title</h3>
  <p class="text-gray-600 leading-relaxed">
    This is a beautiful card built with Tailwind CSS utilities.
  </p>
  <button class="mt-4 bg-blue-500 hover:bg-blue-600 text-white 
                  font-medium py-2 px-4 rounded transition-colors">
    Learn More
  </button>
</div>
