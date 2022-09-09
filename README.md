# Airbnb CSS / Sass სტილისტიკის სახელმძღვანელო

> დედანი: [Airbnb/CSS](https://github.com/airbnb/css)

*ყველაზე გონივრული მიდგომა CSS-ისა და Sass-ის წერისათვის*

## სარჩევი

1. [ტერმინოლოგია](#ტერმინოლოგია)
    - [წესის დეკლარაცია](#წესის-დეკლარაცია)
    - [სელექტორები](#სელექტორები)
    - [თვისებები](#თვისებები)
1. [CSS](#css)
    - [ფორმატირება](#ფორმატირება)
    - [კომენტარები](#კომენტარები)
    - [OOCSS და BEM](#oocss-და-bem)
    - [ID-სელექტორები](#id-სელექტორები)
    - [JavaScript-ჰუკები](#javascript-ჰუკები)
    - [თვისება „Border“](#თვისება-border)
1. [Sass](#sass)
    - [სინტაქსი](#სინტაქსი)
    - [მოწესრიგება](#თვისებათა-განცხადებების-დეკლარაციების-დალაგება)
    - [ცვლადები](#ცვლადები)
    - [მიქსინები](#მიქსინები-mixins)
    - [Extend დირექტივა](#extend-დირექტივა)
    - [ჩადგმული სელექტორები](#ჩადგმული-nested-სელექტორები)
1. [ლიცენზია](#ლიცენზია)

## ტერმინოლოგია

### წესის დეკლარაცია

სელექტორის (ან სელექტორთა ჯგუფის) და მისი თანმხლები თვისებების ერთობლიობას „წესის დეკლარაცია“ ეწოდება. მაგალითი:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

### სელექტორები

წესის დეკლარაციაში „სელექტორი“ არის ის ნაწილი, რომელიც განსაზღვრავს, DOM-ში შემავალი ელემენტებიდან რომლების სტილიზება უნდა მოხდეს განსაზღვრული თვისებებით. სელექტორი შეიძლება შეესაბამებოდეს HTML-ელემენტებს, ასევე ელემენტის კლასს, ID-ს ან მის (*ელემენტის*) ნებისმიერ ატრიბუტს. სელექტორთა გამოყენების მაგალითები:

```css
.my-element-class {
  /* ... */
}
[aria-hidden] {
  /* ... */
}
```

### თვისებები

დაბოლოს, თვისებები წესის დეკლარაციის ის ნაწილია, რომელიც შერჩეულ ელემენტებს სტილს ანიჭებს. თვისებათა ჩაწერა ხდება შემდეგი სახით: `გასაღები: მნიშვნელობა`. წესის დეკლარაცია შეიძლება შეიცავდეს თვისების ერთ ან მეტ განცხადებას (*დეკლარაციას*). თვისებათა განცხადებები ასე გამოიყურება:

```css
/* რაიმე სელექტორი */ {
  background: #f1f1f1;
  color: #333;
}
```

**[⬆ ზემოთ](#სარჩევი)**

## CSS

### ფორმატირება

* აბზაცებისათვის გამოიყენეთ რბილი ჩანართები (2 შუალედი).
* კლასის სახელებში, ე.წ. „კუზიანი ნოტაციის“ (*camelCasing*) ნაცვლად უმჯობესია გამოიყენოთ ტირეები.
  - ქვეტირეები და ე.წ. „პასკალის ნოტაცია“ (*PascalCasing*) დასაშვებია, თუკი იყენებთ BEM-ს (იხილეთ [OOCSS და BEM](#oocss-და-bem)).
* არ გამოიყენოთ ID-სელექტორები.
* როდესაც წესის დეკლარაციაში მრავალ სელექტორს იყენებთ, ყოველი სელექტორი განათავსეთ ახალ ხაზზე.
* წესის დეკლარაციებში, გამხსნელი `{` ფრჩხილის წინ განათავსეთ შუალედი.
* თვისებებში, `:` ორწერტილის შემდეგ განათავსეთ შუალედი (ორწერტილამდე - არა).
* წესის დეკლარაციათა დამხურავი `}` ფრჩხილები განათავსეთ ახალ ხაზზე.
* წესის დეკლარაციები ერთმანეთისაგან გამოყავით ცარიელი ხაზებით.

**ცუდია**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

**კარგია**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}
.one,
.selector,
.per-line {
  // ...
}
```

### კომენტარები

* მრავალსტრიქონიანი კომენტარების ნაცვლად უმჯობესია წეროთ ერთსტრიქონიანი კომენტარები (`//` Sass-ში).
* უმჯობესია კომენტარები განათავსოთ ცალკე ხაზში. მოერიდეთ კომენტარების წერას კოდის სტრიქონის ბოლოში.
* წერეთ დეტალური კომენტარები კოდისათვის, რომელიც საკუთარ თავს გასაგებად არ აღწერს:
  - კოდში გამოყენებულია z-index;
  - კოდი შეიცავს თავსებადობისათვის ან კონკრეტული ბრაუზერისათვის განკუთვნილ „ხრიკებს“.

### OOCSS და BEM

ჩვენ გირჩევთ OOCSS-ისა და BEM-ის გარკვეულ კომბინაციას შემდეგი მიზეზებიდან გამომდინარე:

  * ეს დაგეხმარებათ შექმნათ მკაფიო, მკაცრი ურთიერთობები CSS-სა და HTML-ს შორის;
  * ეს დაგეხმარებათ შექმნათ მრავალჯერადი, კომპოზიტური კომპონენტები;
  * ეს დაგეხმარებათ შეამციროთ ჩადგმების რაოდენობა (*nesting*) და დასწიოთ კონკრეტიკის დონე;
  * ეს დაგეხმარებათ მასშტაბირებადი სტილის ფურცლების (*stylesheets*) შექმნაში.

**OOCSS**, იგივე „ობიექტზე ორიენტირებული CSS“, არის CSS-ის წერის მიდგომა, რომელიც გიბიძგებთ, იფიქროთ თქვენს სტილის ფურცლებზე (*stylesheets*), როგორც „ობიექტთა“ ერთობლიობაზე: მრავალჯერად, განმეორებად კოდის ფრაგმენტებზე, რომლებიც შესაძლებელია ხელახლა იქნეს გამოყენებული დამოუკიდებლად, ვებსაიტის მასშტაბით.

  * Nicole Sullivan-ის [OOCSS wiki](https://github.com/stubbornella/oocss/wiki)
  * Smashing Magazine-ის [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)

**BEM**, იგივე „ბლოკი-ელემენტი-მოდიფიკატორი“, არის *სახელდების კანონზომიერება* კლასებისათვის HTML-სა და CSS-ში. იგი თავდაპირველად შეიმუშავა Yandex-მა, დიდი მოცულობით კოდისა და მასშტაბურობის გათვალისწინებით და, შეიძლება გამოგადგეთ OOCSS-ის რეალიზებისათვის, როგორც მითითებათა საფუძვლიანი ნაკრები.

  * CSS Trick-ის [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts-ის [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

ჩვენ გირჩევთ BEM-ის ვარიანტს „პასკალური ნოტაციის“ (*PascalCased*) „ბლოკებით“, რომელიც მეტადრე კარგად მუშაობს მაშინ, როცა კომბინირებულია კომპონენტებთან (მაგ. React). ქვეტირეები და ტირეები კვლავაც გამოიყენება მოდიფიკატორებისა და შვილობილი ელემენტებისათვის.

**მაგალითი**

```jsx
// ListingCard.jsx
function ListingCard() {
  return (
    <article class="ListingCard ListingCard--featured">
      <h1 class="ListingCard__title">Adorable 2BR in the sunny Mission</h1>
      <div class="ListingCard__content">
        <p>Vestibulum id ligula porta felis euismod semper.</p>
      </div>
    </article>
  );
}
```

```css
/* ListingCard.css */
.ListingCard { }
.ListingCard--featured { }
.ListingCard__title { }
.ListingCard__content { }
```

  * `.ListingCard` არის „ბლოკი“ და წარმოადგენს უმაღლესი დონის (*higher-level*) კომპონენტს.
  * `.ListingCard__title` არის „ელემენტი“ და წარმოადგენს `.ListingCard`-ის შთამომავალს, რაც ბლოკის ერთ მთლიანობად ჩამოყალიბებას უწყობს ხელს.
  * `.ListingCard--featured` არის „მოდიფიკატორი“ და ასახავს ბლოკის მდგომარეობას ან ვარიაციას.

### ID-სელექტორები

მიუხედავად იმისა, რომ CSS-ში ელემენტების შერჩევა (სელექცია) შესაძლებელია ID-ის გამოყენებით, ზოგადად, ეს უნდა ჩაითვალოს ცუდ პრაქტიკად. ID-სელექტორებს თქვენს წესის დეკლარაციებში შემოაქვთ [სპეციფიკურობის](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) ზედმეტად მაღალი დონე და, ამასთანავე მათი ხელახლა გამოყენებაც შეუძლებელია.

ამ თემასთან დაკავშირებით მეტად დეტალური ინფორმაციის მისაღებად იხილეთ შემდეგი სტატია: [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/).

### JavaScript-ჰუკები

მოერიდეთ ერთსა და იმავე კლასთან დაკავშირებას CSS-დან და JavaScript-დან. ამ ორის შერწყმა ხშირად იწვევს, როგორც მინიმუმ, დროის დაკარგვას რეფაქტორირებისას, რადგან დეველოპერს უწევს თითოეული კლასის მნიშვნელობის გარკვევა ვიდრე ცვლილებას შეიტანს, ხოლო უარეს შემთხვევაში, დეველოპერი ფუნქციონირების მოშლის შიშით ყოყმანობს ცვლილებების შეტანას.

ჩვენ გირჩევთ შექმნათ ცალკეული კლასები JavaScript-ისთვის `.js-` თავსართით:

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

### თვისება „Border“

`none`-ის ნაცვლად გამოიყენეთ `0`, რათა მიუთითოთ, რომ სტილს არ გააჩნია ჩარჩო (*border*).

**ცუდია**

```css
.foo {
  border: none;
}
```

**კარგია**

```css
.foo {
  border: 0;
}
```
**[⬆ ზემოთ](#სარჩევი)**

## Sass

### სინტაქსი

* გამოიყენეთ `.scss` სინტაქსი. არასოდეს გამოიყენოთ `.sass` სინტაქსი.
* დაალაგეთ რეგულარული CSS-ი და `@include` განცხადებები ლოგიკურად (იხ. ქვემოთ).

### თვისებათა განცხადებების (დეკლარაციების) დალაგება

1. თვისებათა განცხადებები

    ჩამოთვალეთ ყოველი სტანდარტული თვისებათა განცხადება, ყველაფერი, რაც არ არის `@include` ან ჩადგმული სელექტორი.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
    ```

2. `@include` განცხადებები

    `@include`-ების ბოლოში განთავსება ამარტივებს მთლიანი სელექტორის წაკითხვას.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

3. ჩადგმული (*nested*) სელექტორები

    ჩადგმული სელექტორები (*მათი გამოყენების საჭიროების შემთხვევაში*) თავსდება ბოლოში, და მათ შემდეგ არაფერი უნდა განთავსდეს. დაამატეთ ცარიელი სტრიქონი წესის დეკლარაციებსა და ჩადგმულ სელექტორებს შორის, ასევე მომიჯნავე ჩადგმულ სელექტორებს შორის. გამოიყენეთ იგივე ინსტრუქციები, რომლებიც ზემოთ არის მოცემული ჩადგმული სელექტორებისათვის.

    ```scss
    .btn {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      .icon {
        margin-right: 10px;
      }
    }
    ```

### ცვლადები

უმჯობესია ცვლადის სახელები ჩაწეროთ ტირეების გამოყენებით (მაგ. `$my-variable`), მათი „კუზიანი ნოტაციის“ (*camelCased*) ან ქვეტირეს (*snake_cased*) გამოყენებით ჩაწერის ნაცვლად. დასაშვებია ქვეტირეს თავსართად გამოყენება (მაგ. `$_my-variable`) ისეთი ცვლადების ჩასაწერად, რომელთა გამოყენებაც გათვალისწინებულია მხოლოდ იმავე ფაილის მასშტაბით.

### მიქსინები (*Mixins*)

მიქსინების გამოყენება უნდა მოხდეს კოდისათვის სიცხადის, ან აბსტრაქტული სირთულის შესამატებლად (დაახლოებით იგივენაირად, როგორც ფუნქციებისათვის სახელების სწორად შერჩევისას). მიქსინები, რომლებიც არ იღებენ არგუმენტებს შეიძლება გამოდგეს ამისთვის, მაგრამ გაითვალისწინეთ, რომ თუ თქვენს ფაილს არ შეკუმშავთ (მაგ. gzip), ამან შეიძლება ხელი შეუწყოს კოდის გაუთვალისწინებელ გამეორებას (*დუბლიკაციას*).

### Extend დირექტივა

`@extend`-ის გამოყენებას უნდა მოერიდოთ, რადგან მას ახასიათებს არაინტუიციური და პოტენციურად საშიში ქცევა, განსაკუთრებით მაშინ, როცა ჩადგმულ სელექტორებთან გამოიყენება. ზედა დონის შემავსებელმა (*placeholder*) სელექტორებმაც კი შეიძლება გამოიწვიოს პრობლემები, თუკი სელექტორთა თანმიმდევრობა მოგვიანებით შეიცვლება (მაგ. თუ ისინი განთავსებულია ცალკეულ ფაილებში და ფაილთა ჩატვირთვის თანმიმდევრობა შეიცვლება). შეკუმშვამ (*Gzipping*) უნდა აანაზღაუროს იმ უპირატესობათა უმეტესობა, რომელსაც მიიღებდით `@extend`-ის გამოყენების შემთხვევაში, ხოლო კოდისათვის სიცხადის შემატებისათვის მიქსინები მშვენიერი საშუალებაა.

### ჩადგმული (*nested*) სელექტორები

**სელექტორთა ჩადგმის სიღრმე არ უნდა აღემატებოდეს სამს!**

```scss
.page-container {
  .content {
    .profile {
      // შეჩერდით!
    }
  }
}
```

როდესაც სელექტორები ამსიგრძისა ხდება, სავარაუდოდ, თქვენს მიერ დაწერილი CSS-ი:

* მტკიცედ არის დაკავშირებული HTML-თან (მყიფე); *—ან—*
* მეტისმეტად კონკრეტულია; *—ან—*
* არ არის ხელახლა გამოყენებადი.


კიდევ ერთხელ: **არასოდეს მოახდინოთ ID-სელექტორების ჩადგმა (*nesting*)!**

თუ გიწევთ ID-სელექტორის გამოყენება (რასაც, კარგი იქნება, თუ თავს აარიდებთ), მათი ჩადგმა არასოდეს უნდა მოხდეს. თუ ამის აუცილებლობის წინაშე დადგებით, უმჯობესია, კიდევ ერთხელ გადახედოთ თქვენს მარკირებას (HTML-ს) და გაარკვიოთ, რამ გამოიწვია ასეთი ძლიერი კონკრეტულობის საჭიროება. თუ თქვენი HTML-ი და CSS-ი სწორად იქნება სტრუქტურირებული, ამის გაკეთების საჭიროება **არასოდეს** გექნებათ.

**[⬆ ზემოთ](#სარჩევი)**

## ლიცენზია

(The MIT License)

Copyright (c) 2015 Airbnb

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[⬆ ზემოთ](#სარჩევი)**
