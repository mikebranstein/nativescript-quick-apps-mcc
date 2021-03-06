## App 2: Informational app


### Main page

<h4 class="exercise-start">
    <b>Demo</b>: Adding text to an app
</h4>

First, we'll create a page and add some text.

```xml
<Page>
  <ScrollView>
    <StackLayout>

      <!-- Title -->
      <Label text="Welcome to Tekmo!" class="title" />

      <Label textWrap="true" text="Tekmo is a small online retailer specializing in retro video games sales and services. We're based in Louisville, KY." />

      <!-- Sub Title -->
      <Label text="Our Mission" class="sub-title" />

      <Label textWrap="true" text="We exist to bring our customers the best in retro gaming at an affordable price. We love to revisit and replay the games that shaped our childhoods, and believe that through sharing our love, we can help shape another generation of retro gaming geeks." />
      
      <!-- Sub Title -->
      <Label text="History" class="sub-title" />

      <Label textWrap="true" text="In the early 90's, it all started with Rescue Pups. This multi-player vintage platformer brought the Rambo-style side-scrolling gun fights to life in our living room. True, it was impossible to beat with the 3 lives you got by default, but that's why everyone knew the 50 lives code by heart: up, up, down, down, left, right, left, right, B, A, Start. And if you wanted a friend to play along, you could throw in the Select, Start at the end." />

      <Label textWrap="true" text="After Rescue Pups, it was the classics like Super Marshmallow Man and Vampire Valkyrie. Do you remember them? We do. And we loved it! We hosted sleep overs every weekend throughout the summer, stayed up too late, got in trouble, pretended to fall asleep, then crept downstairs in the middle of the night to continue the fun." />

      <Label textWrap="true" text="As we grew older, the games we played did too, but our love for the originals never stopped, and our passion for sharing these games with our friends and family grew." />

      <Label textWrap="true" text="After many year, we all started having kids of our own, and we found ourselves wanting to raise our kids in our footsteps (without the midnight gaming marathons, of course). We wanted our kids to relive the adventure. Relive the thrills. Relive the classics. Tekmo was born." />

      <Label textWrap="true" text="We remembered how cool it was to get 50 lives, so now our kids could enjoy playing through Rescue Pups for hours." />

      <Label textWrap="true" text="And then there was Vampire Valkyrie: a side-scrolling adventure into the depths of Transylvania seeking out Dracula and his minions. After gathering your supplies in local towns, you embarked on a journey through the countryside to rescue trapped village people. We never forget to bring your stake and darn your garlic. And when we finally meet Dracula face-to-face, holy water didn't save us. And now, the fate of the world is on another 7 year old's shoulders." />

      <Label textWrap="true" text="Lastly, Super Marshmallow Man is the one that pushed us over the edge with its iconic landscapes filled with clouds and wonderous sky scenes. We regularly play through the 12 worlds of Mallow Kingdom while avoiding the hungry Chompers with our friends and families: the best part is still watching someone get too close to the flames and melt!" />    

    </StackLayout>
  </ScrollView>
</Page>
```
<div class="exercise-end"></div>

Now, let's style our app with CSS.

<h4 class="exercise-start">
    <b>Demo</b>: Adding some style
</h4>

Add a file named `main-page.css`. Add the styling:

```css
/* Color the background */
Page {
    background-color: lightblue;
}

/* Give text some room around the edges */
Label {
    margin-left: 10;
    margin-right: 10;
    margin-bottom: 10;
}

/* Make the title stand out */
.title {
    font-size: 30;
    horizontal-align: center;
    margin: 20;
}

/* Sub titles are a bit smaller */
.sub-title {
    font-size: 20;
}
```

<div class="exercise-end"></div>
