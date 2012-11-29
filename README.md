# iCloud Reminders for Ruby

This is a Ruby library to access iCloud reminders.


## Examples

```ruby
# Dump all incomplete reminders.
puts Reminders.select do |r|
  not r.completed?
end
```

```ruby
# Create a new reminder.
Reminders.create "Feed the dog",
  :notes => "If you don't, it will starve to death.",
  :at => DateTime.parse("5:30 PM"),
  :repeat => :daily
```


## Testing

Since this library is designed to interact with a remote API, it uses the lovely
[VCR] [vcr] to keep the tests deterministic and fast. However, because iCloud
requires an [Apple ID] [appleid] to log in, the fixtures generated by VCR cannot
be committed to the public repo. So to run the tests, you'll need to set the
following environment vars:

```
APPLE_ID=
APPLE_PW=
```

And you'll need an Apple ID with the following reminders:

```
Title: Incomplete
Completed: No
```

```
Title: Complete
Completed: Yes
```

I use a totally separate Apple ID for this, because it's entirely possible that
this library will trash your calendar, cancel all of your alarms, turn off your
grandmother's life support, and so on. I'm aware this this is absurd, but I
don't have a better solution right now.


## License

[rb-icloud-reminders] [repo] is free software, available under [the MIT license]
[license].




[repo]:    https://github.com/adammck/gh-news-feed-filters
[license]: https://raw.github.com/adammck/gh-news-feed-filters/master/LICENSE
[vcr]:     https://github.com/myronmarston/vcr
[appleid]: https://appleid.apple.com
