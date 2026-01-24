# 1 Component

- what is Component
- component kay name first letter Capital hona chahiye
- component ek function hota hai jo jsx return karta hai
- component reusable hota hai
- component me javascript/typescript ka under html and css likh sakte hai
- component hamasha render huta ha import nahi
- Ek file pa ek sa ziyada component ho sakta hai

<img width="1354" height="858" alt="image" src="https://github.com/user-attachments/assets/42111403-325d-4153-a963-2156381a6d64" />

# 2 Props

- Props Parameter or Argument hi huta ha
- () pa zarori nahi props likho kuch hi likha sakhta hu
- Control + p sa file switch kar sakhta hu
- Props ek Object ha 

<img width="767" height="424" alt="image" src="https://github.com/user-attachments/assets/eecbb551-6373-42b8-a663-154190eb0631" />
<img width="824" height="469" alt="image" src="https://github.com/user-attachments/assets/863bc3d1-c745-4403-8869-f91bd512ce98" />


# 3 Link

- <a> Anchor is lia use nahi karta q ka page reload hu jata ha.

  <img width="1065" height="564" alt="image" src="https://github.com/user-attachments/assets/ed02f826-dee2-47b2-a211-e09e34dc95b3" />

# 4 Layout
- layout ek samjho react componet hi ha us ka us pa bus upper global.css & Font/Google &
- const inter = Inter({subsets:["latin"]})
- metadata for SEO
- Children ka under jitna bhi page.tsx huta ha woh yaha sa show huta ha Google pa
- Layout Har page pa show huti ha Like Header & Footer
- Ek sa ziyada Layout.tsx file banata hu group ka (group) under make sure ka khali component return hu HTML or Body dubara return na hu HTML or Body sir 1 time huta ha.

<img width="594" height="652" alt="image" src="https://github.com/user-attachments/assets/f5c5d322-3385-4a96-99dd-0dcf89938b81" />

# 5 Dynamic Routing [Dynamic]
- Dynamic jo folder banata ha us page.tsx main ek specil Props huta h, Jis ka under.
- params ka under jo product ha woh [product] woh folder ka name or jo Milk ha woh URL pa jo aaya ga,
- Fetch Metho
- use Await for fetch data
- JsonPlaceholder Fake API
- json() pa conver katna Json pa data aa raha hu ga API sa us ko yeh object pa convert karta h,
  
 ```
  props:{params:{product:"milk"},SearchParams:{}}
  ```
 ```
  (props:{params:{product:string}})
  ```
 ```
  map(()=>{}) $ map((variable,index)=>{}) 
  ```
  
<img width="1002" height="469" alt="image" src="https://github.com/user-attachments/assets/f6fd0e42-7ea2-43d2-a56a-aa507a2f7c0d" />
<img width="985" height="719" alt="image" src="https://github.com/user-attachments/assets/3fff9a54-18b8-41a4-9768-3cc2e52bc069" />
<img width="1168" height="629" alt="image" src="https://github.com/user-attachments/assets/02f87d15-006e-4462-8b68-ebe8d8f2e425" />
<img width="1312" height="431" alt="image" src="https://github.com/user-attachments/assets/54a7e250-be83-4ec3-b295-fd5ea746ea58" />

# 6 Static Page 
- by default page static huta h,
- jab Hunm npm Build karta ha to yeh page banta h
```
Static page (Build Time)fetch("API",{})  & fetch("API",{next:{revalidate:3000} Blog webiste
```
<img width="995" height="654" alt="image" src="https://github.com/user-attachments/assets/d2019e67-b79a-4093-bdb3-a770e640fe51" />

# 7 Dynamic Page
- Ecommerce Website(us hi time server pa data fetch hu ga or page bana ga)
```
Dynamic Page (Build Time)fetch("API",{})  & fetch("API",{cache:"no-store"}
```
<img width="984" height="660" alt="image" src="https://github.com/user-attachments/assets/61001929-4a65-4fa5-8f0e-35527a0c5339" />

# 8 Loading Page
-jis level pa ap ko loadign need
- jisa data fetch ka doran laga do
- File ka name loading.tsx hi huna chahiya
  

# 9 Erro Page
- error file hamasha "use client" hu gi,

  <img width="1030" height="673" alt="image" src="https://github.com/user-attachments/assets/a37f1e41-f9e0-45a4-81bf-293a81b25ea0" />

# 10 Group (group)
-is ka talooq sir structure sa ha,
- layout.tsx jab dosri banao to HTML or Body remove kar dena necha image ha us ki dosri wali,
 
<img width="392" height="323" alt="image" src="https://github.com/user-attachments/assets/c4c51d6a-75e9-4240-940b-cfa963392233" />

<img width="1035" height="657" alt="image" src="https://github.com/user-attachments/assets/8da24dbd-8bfe-46a8-8186-f3bf6ce2ecaf" />

# 11 Image
- loading pehla sa image load kar lata h,
- width or height pixel ko perfect karta h
```
<Image Src={bird} alt="bird" width={40} height={40} loading="lazy"/>
```
```
<Image Src={require('../app/')} alt="bird" width={40} height={40} loading="lazy"/>
```
```
import bird from "../image/bird.jpg"

```

# 12 Usestate (Hook)
- varible ko hum update nahi kar sakhta ha function sa is lia UseState use huta.
- OnClick Ek Event ha
- console is ka browser pa mila ga

<img width="871" height="641" alt="image" src="https://github.com/user-attachments/assets/ceee58ab-d477-46d7-ae68-f4d356a39866" />
 
<img width="885" height="668" alt="image" src="https://github.com/user-attachments/assets/781821c0-68d6-48aa-af24-76229c9ef506" />

# 13 UseEffect (Hook)
- UseEffect ka use ziyada tar Data fetch kal ia use huta h 
- us File ka code ya Component kahalo jis bhi run hu ga to UseEffect ka under ka code Run hu jaya ga
- [] dependency array nahi kesi ka upper depend hu ga
- Ek file pa ek sa  ziyada useEffect hu sakhta h,
-  jab bhi count ki value update hu to fire hu jao yani ka Run hu jao  

```
useEffect(()=>{}, [])
```
<img width="499" height="552" alt="image" src="https://github.com/user-attachments/assets/2c6a78e0-5c49-44b9-9baf-ce284a168725" />
<img width="750" height="654" alt="image" src="https://github.com/user-attachments/assets/434c1425-737f-4059-9028-09843296edfe" />

<img width="787" height="694" alt="image" src="https://github.com/user-attachments/assets/a370d8e6-d000-4c26-9caf-c52f60678aad" />

# 13 OnChange (Event)

- jab hi kuch likho to fire hu jaya yani run hu jaya
- OnChange ka parameter pa hama ek parameter milta ha ( e ) name sa e ek object ha
- e ek object ha us object ka under target huta ha or target sa hum value la sakhta h

```
onChange={(e)=> console.log(e.target.value)}
```
```
onChange(()=>{})
```
<img width="1012" height="372" alt="image" src="https://github.com/user-attachments/assets/a32da76b-d1ad-4b96-a24f-f5e8ba7371c3" />
<img width="1229" height="518" alt="image" src="https://github.com/user-attachments/assets/893dbe27-0ac1-423f-a82e-22b4fd108719" />
<img width="978" height="596" alt="image" src="https://github.com/user-attachments/assets/802186bf-aa8b-4064-be49-13ea9767dfec" />

```
"use client";

import { useState } from "react";

export default function Home() {
  const [inputVal, setInputVal] = useState("");
  const [radioVal, setRadioVal] = useState("");

  return (
    <main className="flex flex-col items-center justify-center gap-6 p-10">
      <h1 className="text-[36px]">On Change Handle</h1>

      {/* Text Input */}
      <input
        type="text"
        value={inputVal}
        placeholder="write some thing here"
        className="border text-[30px] px-3"
        onChange={(e) => setInputVal(e.target.value)}
      />

      <p>{inputVal}</p>

      {/* Radio Buttons */}
      <label>
        <input
          type="radio"
          value="haan"
          name="abc"
          onChange={(e) => setRadioVal(e.target.value)}
        />{" "}
        Yes
      </label>

      <label>
        <input
          type="radio"
          value="nahi"
          name="abc"
          onChange={(e) => setRadioVal(e.target.value)}
        />{" "}
        No
      </label>

      <p>{radioVal}</p>
    </main>
  );
}

```
# Props Drilling
- you can say that props are similar to Function jaisa ap funtion pa data send karta hu Argument sa similar same.
<img width="378" height="316" alt="image" src="https://github.com/user-attachments/assets/853e5aae-614d-4393-8b08-4ac5d7468dfc" />
##  Parents Components
<img width="611" height="423" alt="image" src="https://github.com/user-attachments/assets/c303a8d1-3898-47c6-ae4a-0a029c9d38ad" />

## Child A Components 
<img width="595" height="432" alt="image" src="https://github.com/user-attachments/assets/df5cf09d-04fb-4761-8619-36278af90658" />

## Child B Components 
<img width="928" height="509" alt="image" src="https://github.com/user-attachments/assets/1f2acf3a-27a9-44c0-9afc-a6f7cf2a8c82" />

## Child C Components 
<img width="917" height="398" alt="image" src="https://github.com/user-attachments/assets/313f318a-6751-46c8-940b-77c14af1177b" />

# ladki video
- (1)Create , (2)Provider , (3)Consumer
- Consumer sa value sirf hum bahar function sa hi nikalta h
- is context api also Problematic ?
## Note 
koi bhi value ki bhi component pa provide karni hu to ap sab Provider ka zarya sa value provide kara ga ,sab sa pehla hama context create karna huta ha 
or jis file pa context ki value chahiya to Consumer ka zarya sa nikalta h hum.

<img width="750" height="659" alt="image" src="https://github.com/user-attachments/assets/c9adafae-7678-492f-aed2-a9c50a2e293e" />
jo yeh image ha us ka under <ChildA /> component ha agahr tumha <ChildC /> karwana ha to woh likha do aghar sab pa karwana ha to yaha sab likha do
jo It make ka tha woh layout.tsx pa rap kar da raha tha
<img width="645" height="597" alt="image" src="https://github.com/user-attachments/assets/98751975-a47e-4ede-80da-666c6ee10bce" />

## context api also Problematic ?

<img width="646" height="603" alt="image" src="https://github.com/user-attachments/assets/6d21d991-c8f2-4ae1-a530-66181e26f7ef" />
<img width="1050" height="699" alt="image" src="https://github.com/user-attachments/assets/9c35df20-5942-47f3-b7af-c29493f5a7c2" />

# useContext
<img width="615" height="677" alt="image" src="https://github.com/user-attachments/assets/60ad2712-1bae-4634-bd80-c40b43677976" />
<img width="595" height="530" alt="image" src="https://github.com/user-attachments/assets/4484cc08-6ae1-4019-bf82-10e0325d91f0" />

    
<img width="770" height="439" alt="image" src="https://github.com/user-attachments/assets/8a6132df-b569-485b-830a-9dc55744faae" />

  

# Context Api 

- you have Data
- Context API State Manage karna ka lia huta h.
- Component A -> Component B (Child) -> Component C (Child)
- Page 1 -> Page 2 -> Page3
- yeh hamasha use client hu ga
- provider hum layout pa direct nahi banata q ka us ki waja sa puri file ko "use client " karna padha ga
- Props Driven
- props ka zarya sa bhi provide kar sakhta h but bad practice
- For Example jab bhi component A pa kuch changing hu gi to automatic Component bhi apna ap ko Rerender kara ga yani khud ko bhi re render kara ga
  
## Yeh Image Direact Layout.tsx pa provider ki ha jo ka Rong ha 
<img width="1126" height="808" alt="image" src="https://github.com/user-attachments/assets/72359b6b-348b-4c98-bb0e-c92d288f2bdb" />
<img width="915" height="387" alt="image" src="https://github.com/user-attachments/assets/d2fabbc4-ab0c-4ef1-9b37-20e8f74a2e5d" />


<img width="715" height="531" alt="image" src="https://github.com/user-attachments/assets/5d645744-ec50-4d68-8cc9-65908ee20f7a" />

## Ek Alag file banao like CountProvider.tsx 

<img width="1300" height="656" alt="image" src="https://github.com/user-attachments/assets/2b27e312-bd81-4a24-b096-90551be2499d" />

## Phir Layout.tsx pa Provide karo 
<img width="907" height="650" alt="image" src="https://github.com/user-attachments/assets/d4829f38-fab1-4c79-a161-c6d8b034d577" />



