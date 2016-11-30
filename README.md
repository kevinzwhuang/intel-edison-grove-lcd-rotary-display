# Intel Edison + Grove RGB LCD + Grove Rotary Sensor
---------

In this demo, you will combine the Intel Edison with the Grove RGB LCD display
and the Grove Rotary Sensor to handle angle data on the display as background
colors with number data displayed (between 0 and 255).

## Hardware Setup

Before getting started, make sure that your Edison is completely assembled.
Refer to the [Intel Edison with Arduino expansion board assembly
guide](https://software.intel.com/en-us/assembling-intel-edison-board-with-arduino-expansion-board) if you need help with this.

Then make sure to attach the Grove Base Shield to the Edison, attach the Grove
RGB LCD to one of the two 12C ports on the shield, and attach the Grove Rotary
Sensor to the A0 port.

## Software Setup

You will need the following dependencies installed on your Edison for this to
work:

- johnny-five - An open source JavaScript robotics programming framework.
  Johnny-Five  makes it easier for you to toy with your Edison.
- edison-io - The Intel Edison IO Plugin for Johnny-Five. This is required to
  allow Johnny-Five to interface with your board.

To install these on your Edison, ssh into your board and run the following
command:

```
npm install johnny-five edison-io
```

Once this is done, save the `index.js` file from this repo to your Edison or
git clone this repo by running:

```
git clone git@github.com:kevinzwhuang/intel-edison-grove-lcd-rotary-display.git
```

Note: You can also install the dependencies locally to the repo folder by simply running:

```
cd intel-edison-grove-lcd-rotary-display
npm install
```

However, it's recommended that you install the dependencies the first way so
that you have those packages readily available for any other scripts you might want to
run.

## Run it!

Now to run your LCD display script on your Edison, simply run the following
command inside of your `intel-edison-grove-lcd-rotary-display` folder:

```
node index.js
```

Your LCD display should light up now! Move the rotary sensor back and forth to
change the color and data values that are displayed on the display.

## Troubleshooting

Q: I tried running the script but all I'm seeing in my terminal is "Board -
looking for connected device"?
A: You need to make sure that you are specifying that the board Johnny-Five is
looking for is an Intel Edison. The board variable should look like this:
```js
var board = new five.Board({
	io: new Edison()
});
```

Q: My script is running, but my Grove RGB LCD display only displays the
background color with no text!
A: This is probably a power problem - when the LCD display only receives 3V, it
will only display a background color with no text. Check your power supply to
ensure that it is providing enough power to your Edison (if you're powering it
using a USB cable from your computer, this won't be enough power!). The power adapter that comes
with the Grove should do the job.

Also check to see that your Grove Base Shield is set to 5V and not 3V. Check
this [blog post from Intel for more info](https://blogs.intel.com/evangelists/2015/04/08/how-to-set-intel-edison-voltage-to-3-3v/)
(keep in mind, this is a blog post for instructions to set to 3.3V, you should
be doing the reverse here).
