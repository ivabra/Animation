# Animation
Simplified usage of `UIView.animateWithDuration()` sequences.

```swift
let view = UIView();
let imageView = UIImageView()

Animation()
    .before({
        print("Block execured before whole animation")
    })
    .next()             // First animation
        .duration(1.0)
        .delay(0.2)
        .springDumping(1.0)
        .initialSpringVelocity(10)
        .options(.CurveEaseInOut)
        .animation ({ () -> () in   // First animation in sequence block
            view.transform = CGAffineTransformMakeScale(2, 2)
        })
        .before ({ () -> () in
            print("Block executed before this animation")
        })
        .after ({ () -> () in
            print("Block executed after this animation")
        })
        .done()
    .next()             // Second animation
        .duration(2.0)
        .animation ({ () -> () in  // Second animation in sequence block
            imageView.transform = CGAffineTransformMakeScale(0.5, 0.5)
        }).done()
    .after({ () -> () in
        print("Block executed after whole animation")
    })
    .start(false)            // Run all action without animation
```