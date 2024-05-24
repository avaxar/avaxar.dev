---
layout: post
title: Home
---

## Lorem ipsum dolor sit amet

### Consectetur adipiscing elit

#### Sed do eiusmod tempor incididunt

##### Ut labore et dolore magna aliqua

###### Ut enim ad minim veniam

 **Duis aute** _irure dolor_ ~~in reprehenderit~~ `in voluptate` velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."[^1]
              

[^1]: Trust me, bro.

```d
//              
@safe:

import std.stdio;
static import dsdl2;

void main() {
    // SDL initialization
    dsdl2.loadSO();
    dsdl2.init(everything : true);

    // Prints backend information
    writeln("Version of SDL used: ", dsdl2.getVersion());
    writeln("List of drivers: ", dsdl2.getVideoDrivers());
    writeln("Used driver: ", dsdl2.getCurrentVideoDriver());

    // Creates a simple 800x600 window in the center of the screen, as well as its associated GPU renderer
    // dfmt off
    auto window = new dsdl2.Window("My Window", [dsdl2.WindowPos.centered, dsdl2.WindowPos.centered], [800, 600]);
    auto renderer = new dsdl2.Renderer(window, accelerated : true, presentVSync : true);
    // dfmt on

    // The application loop
    bool running = true;
    while (running) {
        // Gets incoming events
        dsdl2.pumpEvents();
        while (auto event = dsdl2.pollEvent()) {
            // On quit
            if (cast(dsdl2.QuitEvent) event) {
                running = false;
            }
        }

        // Clears the screen with white
        renderer.drawColor = dsdl2.Color(255, 255, 255);
        renderer.clear();

        // Draws a filled red box at the center of the screen
        renderer.drawColor = dsdl2.Color(255, 0, 0);
        renderer.fillRect(dsdl2.Rect(350, 250, 100, 100));

        renderer.present();
    }

    // Quits SDL
    dsdl2.quit();
}
```
