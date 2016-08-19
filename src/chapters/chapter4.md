## App 5: I caught 'em all

My kids love Pokemon, so I had to build them a pokedex app. Let's do it together.

### Navigation

I want to scroll through / navigate between Pokemon. Let's add some navigation. 

<h4 class="exercise-start">
    <b>Demo</b>: Using a grid layout
</h4>

Add a basic grid to the screen. 

```xml
<Page xmlns="http://schemas.nativescript.org/tns.xsd" loaded="onLoaded">
    <GridLayout rows="3*,2*,45*" columns="*,*">

      <!-- 
        left nav
        if you tap anything, the onTap event is called 
        -->
      <Image id="prevNav" row="0" col="0" rowSpan="2"
        src="~/images/left.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="prevNavText" row="0" col="0" tap="{{ onTap }}" 
        orientation="horizontal" horizontalAlignment="center" class="nav nav-prev">

        <!-- Custom font from font-awesome of a Left Arrow -->
        <Label text="&#xf053;" class="font-awesome nav-arrow" />

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="prevId" text="{{ prevId }}" class="nav-id" />
        <Label id="prevNavName" text="{{ prevName }}" class="nav-name" />
      </StackLayout>

      <!-- 
        right nav 
        if you tap anything, the onTap event is called 
        -->
      <Image id="nextNav" row="0" col="1" rowSpan="2"
        src="~/images/right.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="nextNavText" row="0" col="1" tap="{{ onTap }}"
        orientation="horizontal" horizontalAlignment="center" class="nav nav-next">

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="nextNavName" text="{{ nextName }}" class="nav-name" />
        <Label id="nextId" text="{{ nextId }}" class="nav-id" />

        <!-- Custom font from font-awesome of a Right Arrow -->
        <Label text="&#xf054;" class="font-awesome nav-arrow" />
      </StackLayout>

      <!--
        center-aligned Pokemon name
        tapping on the name, calls a text-to-speech
      -->
      <StackLayout orientation="horizontal" row="1" colSpan="2" horizontalAlignment="center"
        tap="{{ onSayName }}">

        <!-- data-bound name and id -->
        <Label id="name" text="{{ name }}" />
        <Label id="id" text="{{ id }}" />

        <Button text="&#xf04b;" class="font-awesome play" tap="{{ onSayName }}" />
      </StackLayout>


    </GridLayout>
</Page>
```

Add the page load event to bind to our data source.

```javascript
var viewModel = require("./pokedex-view-model");
var page;

function onLoaded(args) {
    page = args.object;
    page.bindingContext = viewModel.pokedexViewModel;

    //
    // the pokedex view model has several properties
    // - image of the pokemen, i.e. 001.png
    // - name
    // - description
    // - id number
    // - height
    // - category
    // - weight
    // - stats (HP, Attack, Defense, Special Attack, Special Defense, and Speed)
    // - prev pokemon name & id
    // - next pokemon name & id   
    // - navigate to prev/next pokemon
    // - say the name
    //
}
exports.onLoaded = onLoaded;
```

<div class="exercise-end"></div>

### Data binding images

Now, let's add the data bound image of the Pokemon.

<h4 class="exercise-start">
    <b>Demo</b>: Adding a data bound image
</h4>

Add a data bound image is pretty easy, just add the tag and `{{ }}` syntax.

```xml
<Page xmlns="http://schemas.nativescript.org/tns.xsd" loaded="onLoaded">
    <GridLayout rows="3*,2*,45*" columns="*,*">

      <!-- 
        left nav
        if you tap anything, the onTap event is called 
        -->
      <Image id="prevNav" row="0" col="0" rowSpan="2"
        src="~/images/left.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="prevNavText" row="0" col="0" tap="{{ onTap }}" 
        orientation="horizontal" horizontalAlignment="center" class="nav nav-prev">

        <!-- Custom font from font-awesome of a Left Arrow -->
        <Label text="&#xf053;" class="font-awesome nav-arrow" />

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="prevId" text="{{ prevId }}" class="nav-id" />
        <Label id="prevNavName" text="{{ prevName }}" class="nav-name" />
      </StackLayout>

      <!-- 
        right nav 
        if you tap anything, the onTap event is called 
        -->
      <Image id="nextNav" row="0" col="1" rowSpan="2"
        src="~/images/right.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="nextNavText" row="0" col="1" tap="{{ onTap }}"
        orientation="horizontal" horizontalAlignment="center" class="nav nav-next">

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="nextNavName" text="{{ nextName }}" class="nav-name" />
        <Label id="nextId" text="{{ nextId }}" class="nav-id" />

        <!-- Custom font from font-awesome of a Right Arrow -->
        <Label text="&#xf054;" class="font-awesome nav-arrow" />
      </StackLayout>

      <!--
        center-aligned Pokemon name
        tapping on the name, calls a text-to-speech
      -->
      <StackLayout orientation="horizontal" row="1" colSpan="2" horizontalAlignment="center"
        tap="{{ onSayName }}">

        <!-- data-bound name and id -->
        <Label id="name" text="{{ name }}" />
        <Label id="id" text="{{ id }}" />

        <Button text="&#xf04b;" class="font-awesome play" tap="{{ onSayName }}" />
      </StackLayout>

      <!-- 
        THIRD ROW - Pokemon Info and Stats

        Scroll view with a left and right column
       -->
      <ScrollView row="2" col="0" colSpan="2">
        <!-- content area -->
        <GridLayout rows="auto" columns="*,*">

          <!-- left column -->
          <StackLayout orientation="horizontal" row="0" col="0" class="cell">
            <Border borderRadius="20">
              <Image id="pokemon" src="{{ imageSource }}" stretch="aspectFit" />
            </Border>
          </StackLayout>

          </GridLayout>
        </ScrollView>
    </GridLayout>
</Page>
``` 

<div class="exercise-end"></div>

### Adding more information

Adding more information is an exercise in UI layout. I'll add the right column.

<h4 class="exercise-start">
    <b>Demo</b>: Adding a right column wiht data bound fields
</h4>

```xml
<Page xmlns="http://schemas.nativescript.org/tns.xsd" loaded="onLoaded">
    <GridLayout rows="3*,2*,45*" columns="*,*">

      <!-- 
        left nav
        if you tap anything, the onTap event is called 
        -->
      <Image id="prevNav" row="0" col="0" rowSpan="2"
        src="~/images/left.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="prevNavText" row="0" col="0" tap="{{ onTap }}" 
        orientation="horizontal" horizontalAlignment="center" class="nav nav-prev">

        <!-- Custom font from font-awesome of a Left Arrow -->
        <Label text="&#xf053;" class="font-awesome nav-arrow" />

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="prevId" text="{{ prevId }}" class="nav-id" />
        <Label id="prevNavName" text="{{ prevName }}" class="nav-name" />
      </StackLayout>

      <!-- 
        right nav 
        if you tap anything, the onTap event is called 
        -->
      <Image id="nextNav" row="0" col="1" rowSpan="2"
        src="~/images/right.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="nextNavText" row="0" col="1" tap="{{ onTap }}"
        orientation="horizontal" horizontalAlignment="center" class="nav nav-next">

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="nextNavName" text="{{ nextName }}" class="nav-name" />
        <Label id="nextId" text="{{ nextId }}" class="nav-id" />

        <!-- Custom font from font-awesome of a Right Arrow -->
        <Label text="&#xf054;" class="font-awesome nav-arrow" />
      </StackLayout>

      <!--
        center-aligned Pokemon name
        tapping on the name, calls a text-to-speech
      -->
      <StackLayout orientation="horizontal" row="1" colSpan="2" horizontalAlignment="center"
        tap="{{ onSayName }}">

        <!-- data-bound name and id -->
        <Label id="name" text="{{ name }}" />
        <Label id="id" text="{{ id }}" />

        <Button text="&#xf04b;" class="font-awesome play" tap="{{ onSayName }}" />
      </StackLayout>

      <!-- 
        THIRD ROW - Pokemon Info and Stats

        Scroll view with a left and right column
       -->
      <ScrollView row="2" col="0" colSpan="2">
        <!-- content area -->
        <GridLayout rows="auto" columns="*,*">

          <!-- left column -->
          <StackLayout orientation="horizontal" row="0" col="0" class="cell">
            <Border borderRadius="20">
              <Image id="pokemon" src="{{ imageSource }}" stretch="aspectFit" />
            </Border>
          </StackLayout>


          <!-- right column -->
          <StackLayout row="0" col="1" class="cell">
            <!-- description -->
            <Label id="description" textWrap="true" text="{{ description }}" class="description"
              tap="{{ onReadDescription }}" />

            <!-- info -->
            <GridLayout rows="auto,auto,auto,auto" columns="*,*" class="info-container">
              <Label text="Height" row="0" col="0" class="info info-title" />
              <Label text="{{ height }}" row="1" col="0" class="info info-value" />

              <Label text="Category" row="0" col="1" class="info info-title" />
              <Label text="{{ category }}" row="1" col="1" class="info info-value" />

              <Label text="Weight" row="2" col="0" class="info info-title" />
              <Label text="{{ weight }}" row="3" col="0" class="info info-value" />
            </GridLayout>

            </StackLayout>

          </GridLayout>
        </ScrollView>
    </GridLayout>
</Page>
```

<div class="exercise-end"></div>


### Animations

Now, let's have some fun by adding an animation to show the Pokemon's stats

<h4 class="exercise-start">
    <b>Demo</b>: Adding animation
</h4>

```xml
<Page xmlns="http://schemas.nativescript.org/tns.xsd" loaded="onLoaded">
    <GridLayout rows="3*,2*,45*" columns="*,*">

      <!-- 
        left nav
        if you tap anything, the onTap event is called 
        -->
      <Image id="prevNav" row="0" col="0" rowSpan="2"
        src="~/images/left.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="prevNavText" row="0" col="0" tap="{{ onTap }}" 
        orientation="horizontal" horizontalAlignment="center" class="nav nav-prev">

        <!-- Custom font from font-awesome of a Left Arrow -->
        <Label text="&#xf053;" class="font-awesome nav-arrow" />

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="prevId" text="{{ prevId }}" class="nav-id" />
        <Label id="prevNavName" text="{{ prevName }}" class="nav-name" />
      </StackLayout>

      <!-- 
        right nav 
        if you tap anything, the onTap event is called 
        -->
      <Image id="nextNav" row="0" col="1" rowSpan="2"
        src="~/images/right.png" stretch="fill" tap="{{ onTap }}" />

      <StackLayout id="nextNavText" row="0" col="1" tap="{{ onTap }}"
        orientation="horizontal" horizontalAlignment="center" class="nav nav-next">

        <!-- Data-bound fields between {{ and }}, uses page's bindingContext object -->
        <Label id="nextNavName" text="{{ nextName }}" class="nav-name" />
        <Label id="nextId" text="{{ nextId }}" class="nav-id" />

        <!-- Custom font from font-awesome of a Right Arrow -->
        <Label text="&#xf054;" class="font-awesome nav-arrow" />
      </StackLayout>

      <!--
        center-aligned Pokemon name
        tapping on the name, calls a text-to-speech
      -->
      <StackLayout orientation="horizontal" row="1" colSpan="2" horizontalAlignment="center"
        tap="{{ onSayName }}">

        <!-- data-bound name and id -->
        <Label id="name" text="{{ name }}" />
        <Label id="id" text="{{ id }}" />

        <Button text="&#xf04b;" class="font-awesome play" tap="{{ onSayName }}" />
      </StackLayout>

      <!-- 
        THIRD ROW - Pokemon Info and Stats

        Scroll view with a left and right column
       -->
      <ScrollView row="2" col="0" colSpan="2">
        <!-- content area -->
        <GridLayout rows="auto" columns="*,*">

          <!-- left column -->
          <StackLayout orientation="horizontal" row="0" col="0" class="cell">
            <Border borderRadius="20">
              <Image id="pokemon" src="{{ imageSource }}" stretch="aspectFit" />
            </Border>
          </StackLayout>


          <!-- right column -->
          <StackLayout row="0" col="1" class="cell">
            <!-- description -->
            <Label id="description" textWrap="true" text="{{ description }}" class="description"
              tap="{{ onReadDescription }}" />

            <!-- info -->
            <GridLayout rows="auto,auto,auto,auto" columns="*,*" class="info-container">
              <Label text="Height" row="0" col="0" class="info info-title" />
              <Label text="{{ height }}" row="1" col="0" class="info info-value" />

              <Label text="Category" row="0" col="1" class="info info-title" />
              <Label text="{{ category }}" row="1" col="1" class="info info-value" />

              <Label text="Weight" row="2" col="0" class="info info-title" />
              <Label text="{{ weight }}" row="3" col="0" class="info info-value" />
            </GridLayout>

           <!-- stats -->
            <GridLayout rows="auto,auto" columns="auto,*,*,*,*,*,*,auto" class="stats">
              <Label text="Stats" row="0" col="0" colSpan="8" class="stats-title" />

              <StackLayout row="1" col="0" class="meter-first">
              </StackLayout>

              <StackLayout id="hpMeter" row="1" col="1" class="meter">
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <Label text="HP" textWrap="true" class="meter-label" />
              </StackLayout>

              <StackLayout id="attackMeter" row="1" col="2" class="meter">
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <Label text="Attack" textWrap="true" class="meter-label" />
              </StackLayout>

              <StackLayout id="defenseMeter" row="1" col="3" class="meter">
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <Label text="Defense" textWrap="true" class="meter-label" />
              </StackLayout>

              <StackLayout id="specialAttackMeter" row="1" col="4" class="meter">
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <Label text="Special Attack" textWrap="true" class="meter-label" />
              </StackLayout>

              <StackLayout id="specialDefenseMeter" row="1" col="5" class="meter">
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <Label text="Special Defense" textWrap="true" class="meter-label" />
              </StackLayout>

              <StackLayout id="speedMeter" row="1" col="6" class="meter">
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <StackLayout class="meter-value"></StackLayout>
                <Label text="Speed" textWrap="true" class="meter-label" />
              </StackLayout>

              <StackLayout row="1" col="7" class="meter-last">
              </StackLayout>
            </GridLayout>
            </StackLayout>

          </GridLayout>
        </ScrollView>
    </GridLayout>
</Page>
```

And now the javascript logic to fire the animations:

```javascript
var viewModel = require("./pokedex-view-model");
var colorModule = require("color");
var animationModule = require("ui/animation");
var observableModule = require("data/observable");
var page;

function onLoaded(args) {
    page = args.object;
    page.bindingContext = viewModel.pokedexViewModel;

    //
    // the pokedex view model has several properties
    // - image of the pokemen, i.e. 001.png
    // - name
    // - description
    // - id number
    // - height
    // - category
    // - weight
    // - stats (HP, Attack, Defense, Special Attack, Special Defense, and Speed)
    // - prev pokemon name & id
    // - next pokemon name & id   
    // - navigate to prev/next pokemon
    // - say the name
    //

    //
    // listen for when the data-bound data source has a property changed event, then
    // fire the stats animation
    viewModel.pokedexViewModel
        .addEventListener(observableModule.Observable.propertyChangeEvent, 
            function (args) {
                if (args.propertyName === "stats") {
                    animateStats(args.value);
                } 
            });

    // tell the initial pokemon loaded to animate it's stats
    animateStats(viewModel.pokedexViewModel.stats);

}
exports.onLoaded = onLoaded;

//
// animates the coloring of the stat boxes, based upon the pokemon's stat level
//
// concepts: 
// - fillMeter(): fills a meter up to the level specified 
// - drainMeter(): drains a meter to the level specified
//
// - each function returns a promise for chained commands
// - a start delay and end delay can be added in milliseconds
function animateStats(meterValues) {

    //
    // collection of UI ids for each of the stat meters
    var meterIds = 
        ["hpMeter", "attackMeter", "defenseMeter", 
            "specialAttackMeter", "specialDefenseMeter", "speedMeter"];

    //
    // STEPS
    // 1. drain to zero (resets)
    // 2. pick an initial level to fillto (random)
    // 3. fill to the initial level
    // 4. drain to zero
    // 5. fill to the data-bound stat level
    var controlMeter = function (meter, initialLevel, level, delay) {
        setTimeout(function() {
            drainMeter(meter, 10, 0, 500)
                .then(function() { return fillMeter(meter, 0, initialLevel, 0); })
                .then(function() { return drainMeter(meter, initialLevel, 0, 500); })
                .then(function() { return fillMeter(meter, 0, level, 0); });
        }, delay);
    };
    
    //
    // shuffles an array
    var shuffle = function (array) {
        var currentIndex = array.length, temporaryValue, randomIndex;

        // While there remain elements to shuffle...
        while (0 !== currentIndex) {

            // Pick a remaining element...
            randomIndex = Math.floor(Math.random() * currentIndex);
            currentIndex -= 1;

            // And swap it with the current element.
            temporaryValue = array[currentIndex];
            array[currentIndex] = array[randomIndex];
            array[randomIndex] = temporaryValue;
        }
        return array;
    };

    //
    // STEPS: 
    // 1. establish a start delay of 250 milliseconds 
    // 2. randomize the order in which the stats are anuimated
    // 3. run the animation in the randomized order, passing in a random initial value
    var delay = 0;
    var delayOffset = 250;
    var order = shuffle([0,1,2,3,4,5]);
    for (var i = 0; i < order.length; i++) {
        var initialLevel = Math.floor((Math.random() * 10) + 1);
        controlMeter(meterIds[order[i]], initialLevel, meterValues[order[i]], delay);
        delay += delayOffset;
    }
}



function fillMeter(id, fromLevel, toLevel, beginDelay, endDelay) {
    var meter = getMeterById(id);
    return fillRecurse(meter, toLevel, fromLevel, 1, "#30A7D7", endDelay);
}

function drainMeter(id, fromLevel, toLevel, endDelay) {
    var meter = getMeterById(id);
    return fillRecurse(meter, toLevel-1, fromLevel-1, -1, "white", endDelay);    
}

function fillRecurse(meter, level, current, step, color, endDelay) {
    if (current === level) return new Promise(function(resolve,error) {
        setTimeout(function() {
            resolve();
        }, endDelay);
    });

    //
    // MAGIC HAPPENS HERE
    // call the animate() function of NativeScript, changing the color with a duration
    return meter[current].animate({
        backgroundColor: new colorModule.Color(color),
        duration: 40
    }).then(function() {
        return fillRecurse(meter, level, current+step, step, color, endDelay);
    });
}

function getMeterById(id) {
    var meter = new Array();

    var meterContainer = page.getViewById(id);
    var childrenCount = meterContainer.getChildrenCount();
    for (var i = childrenCount-2; i >= 0; i--) {
        meter[meter.length] = meterContainer.getChildAt(i);
    }

    return meter;
}
```

<div class="exercise-end"></div>

