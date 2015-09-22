## Lightning Components
The Lightning App Builder is a point-and-click tool that makes it easy to create custom app pages for Salesforce1. With the Lightning App Builder, you can combine various components on a single app home page to give your Salesforce1 users what they need all in one place.

## With the Lightning App Builder, you can build:

- Simple, single-page apps with the ability to drill down into the details
- Dashboard-style apps, such as for tracking top sales prospects or key leads for the quarter
- “Point” apps to address a particular task, such as entering and monitoring expenses

- No Code required. 
- 1. Build a new Lightning App 
- 2. Inside, you see a canvas. This a GUI builder. 
- 3. Publisher Actions are nice, quick features. Publisher Actions are supported by Lightning App builder. 
- 4. Click "Activate" to add the app to the Salesforce 1 App.

## Lightning Components

A Lightning component is a compact, configurable, and reusable element that you can drag and drop onto a Lightning Page in the Lightning App Builder.

You can use standard, custom, and third-party components in the Lightning App Builder.

### Standard Components
Standard components are Lightning components built by Salesforce. The Lightning App Builder supports these standard Lightning components.

- Filter List (List View)
- Recent Items
- Report Chart
- Rich Text
- Visualforce Page

### Custom Components
Custom components are Lightning components that you or someone else have created. With some modifications, custom Lightning components can work in the Lightning App Builder. For more information, see the Lightning Components Developer’s Guide.
Third-Party Components on AppExchange
The AppExchange provides a marketplace for Lightning components. You can find packages containing components already configured and ready to use in the Lightning App Builder. https://developer.salesforce.com/docs/atlas.en-us.198.0.lightning.meta/lightning/components_config_for_app_builder.htm

![Lightning Breakdown](https://res.cloudinary.com/hy4kyit2a/image/upload/doc/trailhead/help/images/lightning_app_builder_ui)

####Header (1)
The header shows you the label of your Lightning Page. It also gives you the opportunity to return to Setup without saving or to view additional help for the Lightning App Builder.

####Toolbar (2)
Use the buttons in the toolbar to cut (Cut), copy (Copy), and paste (Paste) page content; and to undo (Undo), redo (Redo), save, or activate your Lightning Page. You can also view your page in different formats and adjust the canvas size to fit your view.

####Lightning Components Pane (3)
The components pane contains all standard and custom Lightning components that are supported for your Lightning Page. Click and drag a component to add it to the page.


####Lightning Page Canvas (4)
The canvas area is where you build your page. You can drag components to reorder them on the page. If a component has missing or invalid properties, you see an invalid component indicator.

####Properties Pane (5)
Depending on what you select on the page, the properties pane shows either the overall page properties or the properties of the component that you’ve selected. Click Page in the breadcrumb to access the page properties when viewing a component


##Actions and Lightning Pages

You can also add global actions to a Lightning Page. Actions allow a user to do things from your Lightning Page, such as:

- record call details, 
- create or update records, 
- send email, 
- or create a task. 

When a user visits a Lightning Page in Salesforce1, the page’s actions appear in its action bar.

To find out more about global actions, visit “Creating Global Quick Actions” in the Salesforce1 Mobile Basics Trailhead module.

## How to Activate and add the App Home Page to Salesforce 1

1. Click Activate.
2. Don’t change the page’s custom tab label.
By default, the label that you give the Lightning Page is used as the label for its custom tab.
3. Change the custom tab’s icon to the blue lightning bolt icon.
The icon that you choose here is used as the icon for the app in Salesforce1.
4. Keep the tab’s visibility open to all users.

```
Tip
Selecting System Administrators Only makes the tab visible to all users with the System Administrator profile. This setting is useful while you're working on your Lightning Page. Restricting your page to only administrators means that you can see and test the page but your users can't see it until you're ready to expose it to them.
```

5. Scroll through the Salesforce1 Navigation Position box to find your page. By default, it’s below Smart Search Items, which means that your page tab appears in the Apps section of the Salesforce1 navigation menu.

6. Click and drag your page tab below the Today menu item.
Activate Your Lightning Page
7. Click Activate.

