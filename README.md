# Unicode Clock

Unicode clock in JavaScript: http://david-risney.github.io/UnicodeClock/

Unicode has code points for all 30 minute increments of clock faces. This is a simple project to display the one closest to the current time written in JavaScript.

Because the code points are all above 0xFFFF, I make use of some ES6 additions. I use the \u{XXXXXX} style escape sequence since the old style JavaScript escape sequence \uXXXX only supports code points up to 0xFFFF. I also use the method String.codePointAt rather than String.charCodeAt because the code points larger than 0xFFFF are represented in JavaScript strings using surrogate pairs and charCodeAt gives the surrogate value rather than codePointAt which gives the code point represented by the pair of surrogates.

    "🕛".codePointAt(0)
    128347
    "🕛".charCodeAt(0)
    55357

🕛🕧🕐🕜🕑🕝🕒🕞🕓🕟🕔🕠🕕🕡🕖🕢🕗🕣🕘🕤🕙🕥🕚🕦

The ordering of the code points does not make it simple to do this. I initally guessed the first code point in the range would be 12:00 followed by 12:30, 1:00 and so on. But actually 1:00 is first followed by all the on the hour times then all the half hour times.
