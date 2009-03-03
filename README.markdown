SCListener 1.0.1
================

A simple class for listening to microphone levels, suitable for the iPhone.

* [Intro](http://stephencelis.com/2009/03/02/now-i-just-need-an-audience.html)
* [GitHub](http://github.com/stephencelis/sc_listener)


Usage
-----

    #import "SCListener.h" // Remember to link to AudioToolbox.framework.
    
    // Start listening.
    [[SCListener sharedListener] listen];
    
    // Retrieve the average power.
    [[SCListener sharedListener] averagePower];
    
    // Retrieve the peak power.
    [[SCListener sharedListener] peakPower];
    
    // Hmm...we're using this guy a lot...
    SCListener *listener = [SCListener sharedListener];
    
    // We can temporarily stop returning levels
    [listener pause];
    [listener listen]; // Quick.
    
    // Or free up resources when we're not listening for awhile.
    [listener stop];
    [listener listen]; // Slower.
    
    // Advanced!:
    //
    // If you're using the average and the peak, fetch both at once.
    if (![listener isListening]) // If listener has paused or stopped...
      return;                    // ...bail.
    
    AudioQueueLevelMeterState *levels = [listener levels];
    Float32 peak = levels[0].mPeakPower;
    Float32 average = levels[0].mAveragePower;


License
-------

(c) 2009-* Stephen Celis, <stephen@stephencelis.com>.

Permission is hereby granted, free of charge, to any person obtaining a copy 
of this software and associated documentation files (the "Software"), to deal 
in the Software without restriction, including without limitation the rights 
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell 
copies of the Software, and to permit persons to whom the Software is 
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
