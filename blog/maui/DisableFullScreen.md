### To disable the Full Screen button on Mac Catalyst follow these steps:

1. Go to `Platforms/MacCatalyst/AppDelegate.cs`.
   
2. And paste the following code:
   ```csharp
    [SuppressMessage("Interoperability", "CA1416:Validate platform compatibility")]
    public override void OnActivated(UIApplication application)
    {
        base.OnActivated(application);
        
        var window = this.GetWindow();

        if (window is { WindowScene.SizeRestrictions: { } sizeRestrictions })
        {
            sizeRestrictions.AllowsFullScreen = false;
        }
    }
   ```
   
3. Now, the Full Screen button should be grayed out.
