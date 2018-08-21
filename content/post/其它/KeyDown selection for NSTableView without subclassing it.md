Title: KeyDown selection for NSTableView without subclassing it

Date: 2013-04-10 23:38:42

Tags: Cocoa , Delegate , keyDown , NSTableView

In [cciN_objc]NSTableView[/cciN_objc], when you move the highlighting by arrow key, you actually performed the row selections.  Same as you left click the row by mouse. This feature is now so pleasing, because sometimes people may want to press enter to select that row, while in default, press enter will perform the editing of the row.

There are lot of interests in altering this feature programmatically. But most of the solutions involve subclassing the [cciN_objc]NSTableView[/cciN_objc]'s [cciN_objc]keyDown:[/cciN_objc] method, which is a bit cumbersome.

Actually, we can make advantage of the existing feature, namely "enter = editing". By looking at the references of [cciN_objc]NSTableView[/cciN_objc], I realized one can override the _delegation_ method:

[ccN_objc]-(BOOL)tableView:(NSTableView *)tableView shouldEditTableColumn:(NSTableColumn *)tableColumn row:(NSInteger)row[/ccN_objc]

to prevent [cciN_objc]NSTableView[/cciN_objc]'s cell entering the _editing_ mode, by letting this method return [cciN_objc]NO[/cciN_objc]. Then you can use

[ccN_objc][sessionTable selectedRow][/ccN_objc]

to get the current selection. Then you can do whatever you want, like the code in the following:

[cc_objc]

// Key Down selection for NSTableView

-(BOOL)tableView:(NSTableView *)tableView shouldEditTableColumn:(NSTableColumn *)tableColumn row:(NSInteger)row{

NSInteger r = [sessionTable selectedRow];

[statusLabel setStringValue:[[NSString alloc] initWithFormat:@"You have selected row:%ld",(long)r]];

Session* s = [[Session alloc] initWithSessionType:(Session*)[sessions objectAtIndex:r]];

if (!s.isLaunched) {

    if ([s launch])

    [s generateSessionInfo];

    [sessions addObject:s];

}

[sessionTable reloadData];

// Always return NO

return NO;

}

[/cc_objc]