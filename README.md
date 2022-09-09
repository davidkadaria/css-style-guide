# Airbnb CSS / Sass Styleguide
# CSS/Sass-ის სტილისტიკის სახელმძღვანელო Airbnb-სგან

> დედანი: [Airbnb/CSS](https://github.com/airbnb/css)

*A mostly reasonable approach to CSS and Sass*
*ყველაზე გონივრული მიდგომა CSS-ისა და Sass-ის წერისათვის*

## Table of Contents
## სარჩევი

1. [Terminology](#terminology)
    - [Rule Declaration](#rule-declaration)
    - [Selectors](#selectors)
    - [Properties](#properties)
1. [CSS](#css)
    - [Formatting](#formatting)
    - [Comments](#comments)
    - [OOCSS and BEM](#oocss-and-bem)
    - [ID Selectors](#id-selectors)
    - [JavaScript hooks](#javascript-hooks)
    - [Border](#border)
1. [Sass](#sass)
    - [Syntax](#syntax)
    - [Ordering](#ordering-of-property-declarations)
    - [Variables](#variables)
    - [Mixins](#mixins)
    - [Extend directive](#extend-directive)
    - [Nested selectors](#nested-selectors)
1. [Translation](#translation)
1. [License](#license)

## Terminology
## ტერმინოლოგია

### Rule declaration
### წესის დეკლარაცია

A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:
სელექტორის (ან სელექტორთა ჯგუფს) და მისი თანმხლები თვისებების ერთობლიობას „წესის დეკლარაცია“ ეწოდება. მაგალითი:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

### Selectors
### სელექტორები

In a rule declaration, “selectors” are the bits that determine which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. Here are some examples of selectors:
წესის დეკლარაციაში „სელექტორი“ არის ის ნაწილი, რომელიც განსაზღვრავს, DOM-ხის რომელი ელემენტების სტილიზება უნდა მოხდეს განსაზღვრული თვისებებით. სელექტორი შეიძლება შეესაბამებოდეს HTML-ელემენტებს, ისევე როგორც ელემენტის კლასს, ID-ს ან მის (*ელემენტის*) ნებისმიერ ატრიბუტს. სელექტორთა გამოყენების მაგალითები:

```css
.my-element-class {
  /* ... */
}
[aria-hidden] {
  /* ... */
}
```

### Properties
### თვისებები

Finally, properties are what give the selected elements of a rule declaration their style. Properties are key-value pairs, and a rule declaration can contain one or more property declarations. Property declarations look like this:
დაბოლოს, თვისებები წესის დეკლარაციაში შერჩეულ ელემენტებს სტილს ანიჭებენ. თვისებათა ჩაწერა ხდება შემდეგი სახით: `გასაღები: მნიშვნელობა`. წესის დეკლარაცია შეიძლება შეიცავდეს თვისების ერთ ან მეტ დეკლარაციას. თვისების დეკლარაციები ასე გამოიყურება:

```css
/* some selector */ /* რაიმე სელექტორი */ {
  background: #f1f1f1;
  color: #333;
}
```

**[⬆ back to top](#table-of-contents)**
**[⬆ ზემოთ](#table-of-contents)**

## CSS

### Formatting
### ფორმატირება

* Use soft tabs (2 spaces) for indentation.
* გამოიყენეთ *რბილი ჩანართები* (soft tabs) აბზაცებისათვის (2 შუალედი).
* Prefer dashes over camelCasing in class names.
  - Underscores and PascalCasing are okay if you are using BEM (see [OOCSS and BEM](#oocss-and-bem) below).
* კლასის სახელებში, ე.წ. „კუზიანი ნოტაციის“ (*camelCasing*) ნაცვლად, უმჯობესია გამოიყენოთ ტირეები.
  - ქვეტირეები და ე.წ. „პასკალის ნოტაცია“ (*PascalCasing*) დასაშვებია, თუკი იყენებთ BEM-ს (იხილეთ [OOCSS და BEM](#oocss-and-bem)).
* Do not use ID selectors.
* არ გამოიყენოთ ID-სელექტორები.
* When using multiple selectors in a rule declaration, give each selector its own line.
* როცა წესის დეკლარაციაში მრავალ სელექტორს იყენებთ, ყოველი სელექტორი განათავსეთ ახალ ხაზზე.
* Put a space before the opening brace `{` in rule declarations.
* წესის დეკლარაციებში, გამხსნელი `{` ფრჩხილის წინ განათავსეთ შუალედი.
* In properties, put a space after, but not before, the `:` character.
* თვისებებში, `:` ორწერტილის შემდეგ განათავსეთ შუალედი (ორწერტილამდე - არა).
* Put closing braces `}` of rule declarations on a new line.
* წესის დეკლარაციათა დამხურავი `}` ფრჩხილები განათავსეთ ახალ ხაზზე.
* Put blank lines between rule declarations.
* წესის დეკლარაციები ერთმანეთისაგან გამოყავით ცარიელი ხაზებით.

**Bad**
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

**Good**
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

### Comments
### კომენტარები

* Prefer line comments (`//` in Sass-land) to block comments.
* უმჯობესია წეროთ ერთსტრიქონიანი კომენტარები (`//` Sass-ში), ნაცვლად მრავალსტრიქონიანისა.
* Prefer comments on their own line. Avoid end-of-line comments.
* უმჯობესია კომენტარები განათავსოთ ცალკე ხაზში. მოერიდეთ კომენტარების წერას კოდის სტრიქონის ბოლოში.
* Write detailed comments for code that isn't self-documenting:
  - Uses of z-index
  - Compatibility or browser-specific hacks
* წერეთ დეტალური კომენტარები კოდისათვის, რომელიც საკუთარ თავს [გასაგებად] არ აღწერს:
  - გამოყენებულია z-index
  - შეიცავს თავსებადობისათვის ან კონკრეტული ბრაუზერისათვის განკუთვნილ *ხრიკებს* (hacks)

### OOCSS and BEM
### OOCSS და BEM

We encourage some combination of OOCSS and BEM for these reasons:
გირჩევთ, OOCSS-ისა და BEM-ის გარკვეულ შეხამებას შემდეგი მიზეზებიდან გამომდინარე:

  * It helps create clear, strict relationships between CSS and HTML
  * ეს გვეხმარება შევქმნათ მკაფიო, მკაცრი ურთიერთობები CSS-სა და HTML-ს შორის;
  * It helps us create reusable, composable components
  * ეს გვეხმარება შევქმნათ მრავალჯერადი, კომპოზიტური კომპონენტები;
  * It allows for less nesting and lower specificity
  * ეს გვეხმარება შევამციროთ ერთმანეთში მოთავსებები (*nesting*) და დავწიოთ სპეციფიკურობის დონე;
  * It helps in building scalable stylesheets
  * ეს გვეხმარება მასშტაბირებადი სტილის ფურცლების (*stylesheets*) შექმნაში.

**OOCSS**, or “Object Oriented CSS”, is an approach for writing CSS that encourages you to think about your stylesheets as a collection of “objects”: reusable, repeatable snippets that can be used independently throughout a website.
**OOCSS**, იგივე „ობიექტზე ორიენტირებული CSS“, არის CSS-ის წერის მიდგომა, რომელიც გიბიძგებთ, იფიქროთ თქვენს სტილის ფურცლებზე (*stylesheets*), როგორც „ობიექტთა“ ერთობლიობაზე: მრავალჯერად, განმეორებად კოდის ფრაგმენტებზე, რომლებიც შესაძლებელია ხელახლა იქნეს გამოყენებული დამოუკიდებლად, ვებსაიტის მასშტაბით.

  * Nicole Sullivan's [OOCSS wiki](https://github.com/stubbornella/oocss/wiki)
  * Nicole Sullivan-ის [OOCSS wiki](https://github.com/stubbornella/oocss/wiki)
  * Smashing Magazine's [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)
  * Smashing Magazine-ის [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)

**BEM**, or “Block-Element-Modifier”, is a _naming convention_ for classes in HTML and CSS. It was originally developed by Yandex with large codebases and scalability in mind, and can serve as a solid set of guidelines for implementing OOCSS.
**BEM**, იგივე „ბლოკი-ელემენტი-მოდიფიკატორი“, არის *სახელდების კანონზომიერება* კლასებისათვის HTML-სა და CSS-ში. იგი თავდაპირველად შეიმუშავა Yandex-მა, დიდი მოცულობით კოდისა და მასშტაბურობის გათვალისწინებით და შეიძლება გამოგადგეთ, როგორც სახელმძღვანელო მითითებათა საფუძვლიანი ნაკრები OOCSS-ის რეალიზებისათვის.

  * CSS Trick's [BEM 101](https://css-tricks.com/bem-101/)
  * CSS Trick-ის [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts' [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
  * Harry Roberts-ის [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

We recommend a variant of BEM with PascalCased “blocks”, which works particularly well when combined with components (e.g. React). Underscores and dashes are still used for modifiers and children.
ჩვენ გირჩევთ BEM-ის ვარიანტს „პასკალური ნოტაციის“ (*PascalCased*) „ბლოკებით“, რომელიც მეტადრე კარგად მუშაობს მაშინ, როცა კომბინირებულია კომპონენტებთან (მაგ. React). ქვეტირეები და ტირეები კვლავაც გამოიყენება მოდიფიკატორებისა და შვილობილი ელემენტებისათვის.

**Example**
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

  * `.ListingCard` is the “block” and represents the higher-level component
  * `.ListingCard` არის „ბლოკი“ და წარმოადგენს უმაღლესი დონის (*higher-level*) კომპონენტს.
  * `.ListingCard__title` is an “element” and represents a descendant of `.ListingCard` that helps compose the block as a whole.
  * `.ListingCard__title` არის „ელემენტი“ და წარმოადგენს `.ListingCard`-ის შთამომავალს, რაც ხელს უწყობს ბლოკის ერთ მთლიანობად ჩამოყალიბებას.
  * `.ListingCard--featured` is a “modifier” and represents a different state or variation on the `.ListingCard` block.
  * `.ListingCard--featured` არის „მოდიფიკატორი“ და წარმოადგენს ბლოკის მდგომარეობას ან ვარიაციას.

### ID selectors
### ID-სელექტორები

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) to your rule declarations, and they are not reusable.
მიუხედავად იმისა, რომ CSS-ში ელემენტების შერჩევა შესაძლებელია ID-ის გამოყენებით, ზოგადად, ეს უნდა ჩაითვალოს ცუდ პრაქტიკად. ID-სელექტორებს თქვენს წესის დეკლარაციებში შემოაქვთ [სპეციფიკურობის](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) ზედმეტად მაღალი დონე და მათი (ID-სელექტორების) ხელახლა გამოყენებაც შეუძლებელია.

For more on this subject, read [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) on dealing with specificity.
ამ თემასთან დაკავშირებით მეტად დეტალური ინფორმაციის მისაღებად იხილეთ შემდეგი სტატია: [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/).

### JavaScript hooks
### JavaScript-ჰუკები

Avoid binding to the same class in both your CSS and JavaScript. Conflating the two often leads to, at a minimum, time wasted during refactoring when a developer must cross-reference each class they are changing, and at its worst, developers being afraid to make changes for fear of breaking functionality.
მოერიდეთ ერთსა და იმავე კლასთან დაკავშირებას თქვენს CSS-სა და JavaScript-ში. ამ ორის შერწყმა ხშირად იწვევს, როგორც მინიმუმ, დროის დაკარგვას რეფაქტორირებისას, რადგან დეველოპერს უწევს თითოეული კლასის მნიშვნელობის გარკვევა, ვიდრე ცვლილებას შეიტანს, ხოლო უარეს შემთხვევაში, დეველოპერი ფუნქციონირების მოშლის შიშით ყოყმანობს ცვლილებების შეტანას.

We recommend creating JavaScript-specific classes to bind to, prefixed with `.js-`:
ჩვენ გირჩევთ შექმნათ ცალკეული კლასები JavaScript-ისთვის `.js-` თავსართით:

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

### Border
### ჩარჩო

Use `0` instead of `none` to specify that a style has no border.
ნაცვლად `none`-ისა, გამოიყენეთ `0`, რათა მიუთითოთ, რომ სტილს არ გააჩნია ჩარჩო (*border*).

**Bad**
**ცუდია**

```css
.foo {
  border: none;
}
```

**Good**
**კარგია**

```css
.foo {
  border: 0;
}
```
**[⬆ back to top](#table-of-contents)**
**[⬆ ზემოთ](#table-of-contents)**

## Sass

### Syntax
### სინტაქსი

* Use the `.scss` syntax, never the original `.sass` syntax
* გამოიყენეთ `.scss` სინტაქსი. არასოდეს გამოიყენოთ ორიგინალი `.sass` სინტაქსი.
* Order your regular CSS and `@include` declarations logically (see below)
* მოაწესრიგეთ ჩვეულებრივი CSS-ი და `@include` დეკლარაციები ლოგიკურად (იხ. ქვემოთ).

### Ordering of property declarations
### თვისებათა დეკლარაციების დალაგება

1. Property declarations
1. თვისებათა დეკლარაციები

    List all standard property declarations, anything that isn't an `@include` or a nested selector.
    ჩამოთვალეთ ყოველი სტანდარტული თვისებათა დეკლარაცია, ყველაფერი, რაც არ არის `@include` ან ჩადგმული (*nested*) სელექტორი.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
    ```

2. `@include` declarations
2. `@include` დეკლარაციები

    Grouping `@include`s at the end makes it easier to read the entire selector.
    `@include`-ების ბოლოში განთავსება ამარტივებს მთლიანი სელექტორის წაკითხვას.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

3. Nested selectors
3. ჩადგმული (*nested*) სელექტორები

    Nested selectors, _if necessary_, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.
    ჩადგმული სელექტორები (*მათი საჭიროების შემთხვევაში*) თავსდება ბოლოში, და მათ შემდეგ არაფერი უნდა განთავსდეს. დაამატეთ ცარიელი სტრიქონი წესის დეკლარაციებსა და ჩადგმულ სელექტორებს შორის, ასევე მომიჯნავე ჩადგმულ სელექტორებს შორის. გამოიყენეთ იგივე ინსტრუქციები, რომლებიც ზემოთ არის მოცემული ჩაშენებული სელექტორებისათვის.

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

### Variables
### ცვლადები

Prefer dash-cased variable names (e.g. `$my-variable`) over camelCased or snake_cased variable names. It is acceptable to prefix variable names that are intended to be used only within the same file with an underscore (e.g. `$_my-variable`).
უმჯობესია ცვლადის სახელები ჩაწეროთ დეფისების გამოყენებით (მაგ.: `$my-variable`), „კუზიანი ნოტაციის“ (*camelCased*) ან ქვეტირეს (*snake_cased*) გამოყენებით ჩაწერილი სახელების ნაცვლად. დასაშვებია ქვეტირეს თავსართად გამოყენება (მაგ.: `$_my-variable`) ისეთი ცვლადების ჩასაწერად, რომელთა გამოყენებაც გათვალისწინებულია მხოლოდ იმავე ფაილის მასშტაბით.

### Mixins
### მიქსინები (*Mixins*)

Mixins should be used to DRY up your code, add clarity, or abstract complexity--in much the same way as well-named functions. Mixins that accept no arguments can be useful for this, but note that if you are not compressing your payload (e.g. gzip), this may contribute to unnecessary code duplication in the resulting styles.
მიქსინების გამოყენება უნდა მოხდეს კოდისათვის სიცხადის, ან აბსტრაქტული სირთულის შესამატებლად (დაახლოებით იგივენაირად, როგორც ფუნქციებისათვის სახელების სწორად შერჩევისას). მიქსინები, რომლებიც არ იღებენ არგუმენტებს, შეიძლება ამისთვის გამოდგეს, მაგრამ გაითვალისწინეთ, რომ თუ თქვენს ფაილს არ შეკუმშავთ (მაგ. gzip), ამან შეიძლება ხელი შეუწყოს კოდის გაუთვალისწინებელ გამეორებას (*დუბლიკაციას*).

### Extend directive
### @extend მითითება

`@extend` should be avoided because it has unintuitive and potentially dangerous behavior, especially when used with nested selectors. Even extending top-level placeholder selectors can cause problems if the order of selectors ends up changing later (e.g. if they are in other files and the order the files are loaded shifts). Gzipping should handle most of the savings you would have gained by using `@extend`, and you can DRY up your stylesheets nicely with mixins.
`@extend` თავიდან უნდა იქნეს აცილებული, რადგან მას ახასიათებს არაინტუიციური და პოტენციურად საშიში ქცევა, განსაკუთრებით მაშინ, როცა ჩადგმულ სელექტორებთან გამოიყენება. ზედა დონის placeholder (*შემავსებელი*) სელექტორებმაც კი შეიძლება გამოიწვიოს პრობლემები, თუკი სელექტორთა თანმიმდევრობა მოგვიანებით შეიცვლება (მაგ.: თუ ისინი განთავსებულია ცალკეულ ფაილებში და ფაილთა ჩატვირთვის თანმიმდევრობა იცვლება). შეკუმშვამ (*Gzipping*) უნდა აანაზღაუროს იმ მოგებათა უმეტესობა, რომელსაც მიიღებდით `@extend`-ის გამოყენების შემთხვევაში, ხოლო კოდისათვის სიცხადის შემატებისათვის მშვენიერი საშუალებაა - მიქსინები.

### Nested selectors
### ჩადგმული (*nested*) სელექტორები

**Do not nest selectors more than three levels deep!**
**ჩადგმულ სელექტორთა სიღრმე არ უნდა აღემატებოდეს სამს!**

```scss
.page-container {
  .content {
    .profile {
      // STOP! // შეჩერდით!
    }
  }
}
```

When selectors become this long, you're likely writing CSS that is:
როდესაც წერთ ასეთი სიგრძის სელექტორებს, სავარაუდოდ წერთ CSS-ს, რომელიც:

* Strongly coupled to the HTML (fragile) *—OR—*
* მტკიცედ არის დაკავშირებული HTML-თან (მყიფე); *—ან—*
* Overly specific (powerful) *—OR—*
* მეტისმეტად კონკრეტულია; *—ან—*
* Not reusable
* არ არის ხელახლა გამოყენებადი.


Again: **never nest ID selectors!**
კიდევ ერთხელ: **არასოდეს ჩადგათ (*nest*) ID-სელექტორები!**

If you must use an ID selector in the first place (and you should really try not to), they should never be nested. If you find yourself doing this, you need to revisit your markup, or figure out why such strong specificity is needed. If you are writing well formed HTML and CSS, you should **never** need to do this.
თუ გიწევთ ID-სელექტორის გამოყენება (რასაც კარგი იქნება, თუ თავს აარიდებთ), მათი ჩადგმა არასოდეს უნდა მოხდეს. თუ ამის აუცილებლობის წინაშე დადგებით, უმჯობესია, კიდევ ერთხელ გადახედოთ თქვენს markup-ს (HTML-ს) და გაარკვიოთ, რამ გამოიწვია ასეთი ძლიერი კონკრეტულობის (სიზუსტის) საჭიროება. თუ თქვენი HTML-ი და CSS-ი სწორად იქნება სტრუქტურირებული, ამის გაკეთება **არასოდეს** დაგჭირდებათ.

**[⬆ back to top](#table-of-contents)**
**[⬆ ზემოთ](#table-of-contents)**

## License
## ლიცენზია

(The MIT License)

Copyright (c) 2015 Airbnb

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[⬆ back to top](#table-of-contents)**
**[⬆ ზემოთ](#table-of-contents)**
