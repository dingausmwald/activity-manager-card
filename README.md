# Activity Manager Card - Updated Version

This is an updated version of the Activity Manager Card that works with the new state-based Activity Manager integration. The card now uses entity states (scheduled/due/overdue) instead of date calculations.

# activity-manager-card

A Lovelace card designed as a companion to the [Activity Manager](https://github.com/dingausmwald/activity-manager) component.

## Installation

### Manually

1. Copy activity-manager.js into your `<config>/<www>` folder
2. Add `activity-manager.js` as a dashboard resource.

### HACS

1. Open the HACS section of Home Assistant.
2. Click the "..." button in the top right corner and select "Custom Repositories."
3. In the window that opens paste this Github URL: `https://github.com/dingausmwald/activity-manager-card`
4. Select "Lovelace"
5. In the window that opens when you select it click om "Install This Repository in HACS"

## Usage

| Field       | Required | Description                                                                |
| ----------- | -------- | -------------------------------------------------------------------------- |
| header      | no       | Title of the card                                                          |
| category    | no       | Filter activities to a specific category                                   |
| mode        | no       | Set to "manage" if you want the manager interface. Defaults to basic mode. |
| icon        | no       | Icon to show on card                                                       |
| showDueOnly | no       | Set to `true` and only activities that are due is shown                    |
| actionTitle | no       | Set the text of the action button. Defaults to "Did it!".                  |
| soonHours   | no       | Style activities that are due within `soonHours`. Defaults to 24 hours.    |

```
type: custom:activity-manager-card
header: Home
category: Home
mode: manage
```

<p align="center">
  <img width="300" src="images/manager.png">
</p>

```
type: custom:activity-manager-card
header: Home
category: Home
```

<p align="center">
  <img width="300" src="images/basic.png">
</p>

## Customization

If you want to customize the card style, you can use [Lovlace Card Mod](https://github.com/thomasloven/lovelace-card-mod). Here are some classes:

| Class         | Description                                              |
| ------------- | -------------------------------------------------------- |
| .am-grid      | Adjust the grid layout of the activities                 |
| .am-item-name | Style activity name                                      |
| .am-due-date  | Style the due date column                                |
| .am-due       | Style the date if it's due. By default, the text is red. |
| .am-action    | Style the action column                                  |

## Changes in this version

-   Uses entity states (configurable terms like scheduled/due/overdue) instead of date calculations
-   State calculations are now handled by the Activity Manager integration
-   Card displays the current state and relative time based on `last_completed` attribute
-   `showDueOnly` and `soonHours` options work with the new state system

## More information

-   Activities are stored in .activities_list.json in your `<config>` folder
-   An entity is created for each activity (e.g. `activity_manager.<category>_<activity>`). The state uses configurable terms (default: scheduled/due/overdue). You can use this entity to build notifications or your own custom cards.
