# ReviewKit

Request reviews only from users with enough recent positive activity and only at appropriate times.


## Requirements

* Minimum deployment target iOS 11+, macOS 10.14+
* Swift 5.8+ (Xcode 14.3+) 


## Usage

1. Add ReviewKit to your app using SwiftPM:
   
   ```
   https://github.com/FlineDev/ReviewKit.git
   ```

2. (Optional) Adjust the criteria by which app reviews are requested on app start (defaults to 3 positive events & expiration after 14 days):

   ```Swift
   import ReviewKit
   // ...
   ReviewKit.criteria = ReviewCriteria(minPositiveEventsWeight: 5, eventsExpireAfterDays: 30)
   ```

3. Determine common workflows in your app and when a user completes one of them, call this:

   ```Swift
   ReviewKit.recordPositiveEventAndRequestReviewIfCriteriaMet()
   ```

4. (Optional) Determine other activities that you think are positive experiences for your users. If they are in the middle of workflows, instead of the above call:

   ```Swift
   ReviewKit.recordPositiveEvent()  // optionally, you can pass a custom `weight` parameter, defaults to 1
   ```

That's it – you have configured App Review requests for your app!

Note that ReviewKit is using Apple's `SKStoreReviewController` API internally. That API already encapsulates some logic to make sure not to ask users too often.


## Showcases

I extracted this library _from_ and use it directly _in_ the following apps (check them out to support me!):

* [RemafoX: Easy App Localization](https://remafox.app/)
* [Twoot it! – Schedule Posts](https://twoot-it.app/)


## License

This library is released under the MIT License. See LICENSE for details.
