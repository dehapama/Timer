1.0
Library as downloaded 02Feb2012 22:55 UTC from http://srmonk.blogspot.com/2012/01/arduino-timer-library.html

1.1
Changed data types of variables and functions:
 o event types and indexes changed from int to int8_t.
 o periods and durations changed from lon to unsigned long.
 o update() and stop() functions typed as void, since they return nothing.
 o pin numbers and pin values changed from int to uint8_t, this agrees with digitalWrite().
 o added return values to Timer::pulse() and Timer::oscillate(uint8_t, unsigned long, uint8_t).
 o changed test in Event::update() to use subtraction to avoid rollover issues.
Updated keywords.txt file to include all functions.

1.2 by Damian Philipp
 o Added a range check to Timer::stop() to avoid memory corruption.
 o Added constants to <Timer.h>: 
    - NO_TIMER_AVAILABLE: Signals that while an event was to be queued, no free timer could be found.
    - TIMER_NOT_AN_EVENT: Can be used to flag a variable that *might* contain a timer ID as *not* containing a timer ID
 o Replaced a bunch of magic numbers in <Timer.cpp> by the above constants
 o Added several comments
 o Added Timer::pulseImmediate(). pulseImmediate sets the pin to the specified value for the given
   duration. After the duration, the pin is set to !value.

1.3 by Martin Pahl
 o Removed Timer::pulseImmediate() and 
 o Fixed Timer::pulse(). A pulse should be send immediately, not after a
   delay. So I think, it's a bug in the original pulse function and there is
   no need for another pulse function.
 o Added optional callback functionality to Timer::oscillate (the version with limited
   repeatition) and Timer::pulse(). The callback function is called at the end
   of the pulse or oscillation.
