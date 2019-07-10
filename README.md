[![Build Status](https://travis-ci.org/ZebraFlesh/ember-cli-happy-splitter.svg?branch=master)](https://travis-ci.org/ZebraFlesh/ember-cli-happy-splitter)
[![npm version](https://img.shields.io/npm/v/ember-cli-happy-splitter.svg)](https://www.npmjs.com/package/ember-cli-happy-splitter)


This fork just make this plugin work with ember 3.10

# ember-cli-happy-splitter

Ember component that implements a split panel (AKA split view, split container).  It tries to have very little opinion 
 about the container and the nested views.
 
Why is it happy?  Because there are no content security policy violations! &#9786;

## Installation

Via Ember CLI:

`ember install ember-cli-happy-splitter`

## Available Options

* `isVertical` - boolean flag to create vertical (true) or horizontal (false) split views; set on the `happy-split-container`
* `splitterWidth` - the width of the splitter in pixels; set on the `happy-split-container`
* `splitPercentage` - the percentage of each `happy-split-view`; you are responsible for ensuring they total 100
* `minimumPercentage` - the minimum `splitPercentage` of each `happy-split-view`; defaults to 10%

### CSS rules

Override the following CSS rules to customize the appearance of this component:

* `.happy-split-container` - the container that holders the views and splitter bars; 100% width and height by default
* `.happy-split-view` - the views within the split container; no default rule provided
* `.happy-splitter` - the splitter bar when the user is not interacting with it
* `.happy-splitter:hover` - the splitter bar when the user is hovering over it; no default rule provided
* `.happy-splitter.dragging` - the splitter bar when the user is dragging it
* `.happy-splitter.vertical, .happy-split-container.vertical.dragging` - change the cursor definition here for vertically split containers
* `.happy-splitter.horizontal, .happy-split-container.horizontal.dragging` - change the cursor definition here for horizontally split containers
* `.happy-splitter-thumb` - the thumb within the splitter bar; no styling by default, refer to 
[splitter-thumb.scss](https://github.com/ZebraFlesh/ember-cli-happy-splitter/tree/master/tests/dummy/app/styles/splitter-thumb.scss) for an example 

## Usage 

This is a simple vertical splitter configuration. Note the use of the handlebars whitespace control character ('~') on 
both sides of the happy-splitter-bar. The happy-split-container uses a simple inline-block layout. When using a 
vertical splitter, browsers will interpret the line breaks as meaningful syntax. The whitespace control character 
removes these line breaks. This is only required for vertical splitters.

````htmlbars
{{#happy-split-container}}
  {{#happy-split-view}}
    <h2>hello from left panel!</h2>
  {{/happy-split-view}}
  {{~ happy-splitter-bar ~}}
  {{#happy-split-view}}
    <h2>hello from right panel!</h2>
  {{/happy-split-view}}
{{/happy-split-container}}
````

### Examples

#### Vertical Splitter

````htmlbars
{{#happy-split-container isVertical=true}}
  {{#happy-split-view}}
    <h2>hello from left panel!</h2>
  {{/happy-split-view}}
  {{~ happy-splitter-bar ~}}
  {{#happy-split-view}}
    <h2>hello from right panel!</h2>
  {{/happy-split-view}}
{{/happy-split-container}}
````

The isVertical variable defaults to true and is optional in this scenario.

#### Horizontal Splitter

````htmlbars
{{#happy-split-container isVertical=false}}
  {{#happy-split-view}}
    <h2>hello from top panel!</h2>
  {{/happy-split-view}}
  {{happy-splitter-bar}}
  {{#happy-split-view}}
    <h2>hello from bottom panel!</h2>
  {{/happy-split-view}}
{{/happy-split-container}}
````

#### Customizing Splitter Width

````htmlbars
{{#happy-split-container isVertical=true splitterWidth=10}}
  {{#happy-split-view}}
    <h2>hello from left panel!</h2>
  {{/happy-split-view}}
  {{~ happy-splitter-bar ~}}
  {{#happy-split-view}}
    <h2>hello from right panel!</h2>
  {{/happy-split-view}}
{{/happy-split-container}}
````

This will create a splitter 10px wide.

#### Customizing Split Amounts

````htmlbars
{{#happy-split-container isVertical=true}}
  {{#happy-split-view splitPercentage=25}}
    <h2>hello from left panel!</h2>
  {{/happy-split-view}}
  {{~ happy-splitter-bar ~}}
  {{#happy-split-view}}
    <h2>hello from right panel!</h2>
  {{/happy-split-view}}
{{/happy-split-container}}
````

Annotate each panel with the desired split percentage. Percentages need to add up to 100.

## To Do

* Add more example templates to the dummy app
* Handle more than 2 panels in a container
* Validate split percentages add up to 100
* Validate minimumPercentage >= 0

## License

MIT license
