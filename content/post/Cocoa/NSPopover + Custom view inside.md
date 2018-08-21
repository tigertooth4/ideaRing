Title: NSPopover + Custom view inside

Date: 2013-04-09 11:21:32

Today I would like to implement a [cciN_objc]NSPopover[/cciN_objc] view with a subclass of [cciN_objc]NSTableView[/cciN_objc] in it.

Here is a solution of how to display [cciN_objc]NSPopover[/cciN_objc] programmatically from stackoverflow : [http://stackoverflow.com/questions/7858765/how-to-create-nspopover-programmatically](http://stackoverflow.com/questions/7858765/how-to-create-nspopover-programmatically) , I'll quote the code below:

[cc_objc]

NSViewController *controller = [[NSViewController alloc] initWithNibName:@"View" bundle:nil];

NSPopover *popover = [[NSPopover alloc] init];

[popover setContentSize:NSMakeSize(100.0f, 100.0f)];

[popover setContentViewController:controller];

[popover setAnimates:YES];

[popover showRelativeToRect:[sender bounds] ofView:sender preferredEdge:NSMaxXEdge];

[popover release];

[controller release];

[/cc_objc]

And here's the comment, which seems to be very important for this implementation:

> The problem is not in NSPopover; the exception is thrown by NSViewController, and it says that although nib load was successful, it's view property is still nil.>

>

> Open “View.nib” in Interface Builder and assign File Owner's view outlet to the view object that the controller is supposed to represent (NSViewContoller becomes the file owner when it loads a nib). This is done by Ctrl-dragging from File Owner icon to the view's icon, then choosing view from the list of outlets.

Here is another link, which I think could be helpful:

[https://www.gargoylesoft.com/blog/2011/08/using-nspopover/](https://www.gargoylesoft.com/blog/2011/08/using-nspopover/).

The problem now seems I haven't set [cciN_objc]contentViewController[/cciN_objc] for the [cciN_objc]NSPopover[/cciN_objc] . I'll check it.