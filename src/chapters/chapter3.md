## App 4: Product listing

### Product page

<h4 class="exercise-start">
    <b>Demo</b>: Using a grid layout
</h4>

Add a simple grid to the Products page.

```xml
<Page>
  <ScrollView>
    <GridLayout rows="*,*,*,*" columns="*,*" width="300" height="600">

        <!-- highlighted product -->    
        <StackLayout row="0" col="0" colSpan="2" class="tile highlight">

        </StackLayout>

        <!-- Couch Commander -->
        <StackLayout row="1" col="0" class="tile">

        </StackLayout>

        <!-- Mummy Madness -->
        <StackLayout row="1" col="1" class="tile">

        </StackLayout>

        <!-- Pyro Robots -->
        <StackLayout row="2" col="0" class="tile">

        </StackLayout>

        <!-- Rescue Pups -->
        <StackLayout row="2" col="1" class="tile">

        </StackLayout>

        <!-- Vampire Valkyrie -->
        <StackLayout row="3" col="0" class="tile">

        </StackLayout>
    </GridLayout>
  </ScrollView>
</Page>
```

Add some styling to the `app.css` file.

```
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

/* Give the page a default background color */
Page {
    background-color: #EFEFEF;
}

/* color each tile's background */
.tile {
    background-color: #FFFFFF;
    margin: 2;
}
```

<div class="exercise-end"></div>

We should add a title for each product we're selling

<h4 class="exercise-start">
    <b>Demo</b>: Adding a title to the tiles
</h4>

Add stack layouts and labels for each game title

```xml
<Page>
  <ScrollView>
    <GridLayout rows="*,*,*,*" columns="*,*" width="300" height="600">

        <!-- highlighted product -->    
        <StackLayout row="0" col="0" colSpan="2" class="tile highlight">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Super Marshmallow Man" textWrap="true" />
            </StackLayout>

        </StackLayout>

        <!-- Couch Commander -->
        <StackLayout row="1" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Couch Commander" textWrap="true" /> 
            </StackLayout>

        </StackLayout>

        <!-- Mummy Madness -->
        <StackLayout row="1" col="1" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Mummy Madness" textWrap="true" /> 
            </StackLayout>

        </StackLayout>

        <!-- Pyro Robots -->
        <StackLayout row="2" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Pyro Robots" textWrap="true" /> 
            </StackLayout>

        </StackLayout>

        <!-- Rescue Pups -->
        <StackLayout row="2" col="1" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Rescue Pups" textWrap="true" /> 
            </StackLayout>

        </StackLayout>

        <!-- Vampire Valkyrie -->
        <StackLayout row="3" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Vampire Valkyrie" textWrap="true" /> 
            </StackLayout>

        </StackLayout>
    </GridLayout>
  </ScrollView>
</Page>
```

Now, style the titles.

```
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

/* Give the page a default background color */
Page {
    background-color: #EFEFEF;
}

/* color each tile's background */
.tile {
    background-color: #FFFFFF;
    margin: 2;
}

/* solid band across the top of each tile */
.tile-title {
    background-color: #99ccff;
}

/* the title of each game */
.tile-title Label {
    font-size: 14;
    color: black;
    margin-top: 5;
}
```

<div class="exercise-end"></div>

Now, let's add an image and a price.

<h4 class="exercise-start">
    <b>Demo</b>: Adding a game image and price
</h4>

Add an `<Image />` tag to each of the tiles.

```xml
<Page>
  <ScrollView>
    <GridLayout rows="*,*,*,*" columns="*,*" width="300" height="600">

        <!-- highlighted product -->    
        <StackLayout row="0" col="0" colSpan="2" class="tile highlight">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Super Marshmallow Man" textWrap="true" />
            </StackLayout>

            <!-- tile content goes here -->
            <Image src="res://supermarshmallowman" />
            <Label textWrap="true" text="Escape from certain death in this wild adventure!" />
            <Label text="$34.99" class="price" />

        </StackLayout>

        <!-- Couch Commander -->
        <StackLayout row="1" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Couch Commander" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://couchcommander" />
            <Label text="$24.99" class="price" />
        </StackLayout>

        <!-- Mummy Madness -->
        <StackLayout row="1" col="1" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Mummy Madness" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://mummymadness" />
            <Label text="$32.99" class="price" />
        </StackLayout>

        <!-- Pyro Robots -->
        <StackLayout row="2" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Pyro Robots" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://pyrorobots" />
            <Label text="$19.99" class="price" />
        </StackLayout>

        <!-- Rescue Pups -->
        <StackLayout row="2" col="1" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Rescue Pups" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://rescuepups" />
            <Label text="$9.99" class="price" />
        </StackLayout>

        <!-- Vampire Valkyrie -->
        <StackLayout row="3" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Vampire Valkyrie" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://vampirevalkyrie" />
            <Label text="$21.99" class="price" />
        </StackLayout>
    </GridLayout>
  </ScrollView>
</Page>
```

And style the images to be smaller, also coloring the price green.

```
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

/* Give the page a default background color */
Page {
    background-color: #EFEFEF;
}

/* color each tile's background */
.tile {
    background-color: #FFFFFF;
    margin: 2;
}

/* solid band across the top of each tile */
.tile-title {
    background-color: #99ccff;
}

/* the title of each game */
.tile-title Label {
    font-size: 14;
    color: black;
    margin-top: 5;
}

/* make the price stand out and align to the right */
.price {
    color: #009933;
    text-align: right;
}

/* shrink images a bit */
Image {
    width: 80;
    height: 80;
}
```

<div class="exercise-end"></div>

The highlighted tile has text scrolling out, so let's re-organize.

<h4 class="exercise-start">
    <b>Demo</b>: Refactoring the highlighted tile
</h4>

Lastly, let's make the highlighted tile look fancy.

```xml
<Page>
  <ScrollView>
    <GridLayout rows="*,*,*,*" columns="*,*" width="300" height="600">

        <!-- highlighted product -->    
        <StackLayout row="0" col="0" colSpan="2" class="tile highlight">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Super Marshmallow Man" textWrap="true" />
            </StackLayout>

            <!-- align content horizontally image on the left, content on the right -->
            <StackLayout orientation="horizontal">
                
                <!-- image on the left -->
                <Image src="res://supermarshmallowman" />

                <!-- content is on the right in a vertical orientation -->
                <StackLayout>
                    <Label textWrap="true" text="Escape from certain death in this wild adventure!" />
                    <Label text="$34.99" class="price" />
                </StackLayout>
            </StackLayout>
        </StackLayout>

        <!-- Couch Commander -->
        <StackLayout row="1" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Couch Commander" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://couchcommander" />
            <Label text="$24.99" class="price" />
        </StackLayout>

        <!-- Mummy Madness -->
        <StackLayout row="1" col="1" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Mummy Madness" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://mummymadness" />
            <Label text="$32.99" class="price" />
        </StackLayout>

        <!-- Pyro Robots -->
        <StackLayout row="2" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Pyro Robots" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://pyrorobots" />
            <Label text="$19.99" class="price" />
        </StackLayout>

        <!-- Rescue Pups -->
        <StackLayout row="2" col="1" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Rescue Pups" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://rescuepups" />
            <Label text="$9.99" class="price" />
        </StackLayout>

        <!-- Vampire Valkyrie -->
        <StackLayout row="3" col="0" class="tile">

            <!-- solid band at top of tile with title -->
            <StackLayout class="tile-title">
                <Label text="Vampire Valkyrie" textWrap="true" /> 
            </StackLayout>

            <!-- tile contents here -->
            <Image src="res://vampirevalkyrie" />
            <Label text="$21.99" class="price" />
        </StackLayout>
    </GridLayout>
  </ScrollView>
</Page>
```

And style.

```
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

/* Give the page a default background color */
Page {
    background-color: #EFEFEF;
}

/* color each tile's background */
.tile {
    background-color: #FFFFFF;
    margin: 2;
}

/* solid band across the top of each tile */
.tile-title {
    background-color: #99ccff;
}

/* the title of each game */
.tile-title Label {
    font-size: 14;
    color: black;
    margin-top: 5;
}

/* make the price stand out and align to the right */
.price {
    color: #009933;
    text-align: right;
}

/* shrink images a bit */
Image {
    width: 80;
    height: 80;
}

/* the first top element should be more prominent
   override the existing tile styles */
.highlight .tile-title {
    font-weight: bold;
    background-color: #6699ff;
}

.highlight .tile-title Label {
    font-size: 18;
}

.highlight .price {
    font-weight: bold;
    color: red;
}

.highlight Image {
    width: 100;
    height: 100;
}
```




<div class="exercise-end"></div>


<h4 class="exercise-start">
    <b>Demo</b>: Using a grid layout
</h4>



<div class="exercise-end"></div>
