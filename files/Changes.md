# Detailed Changes between DUI and MUI v3.2.3 to v3.2.4

## Added Files

### Recipe Book System
1. `vdx/ui_data/container/smelt_recipe_book/smelt_slot_input.uidx` (36 lines)
```json
{
  "namespace": "smelt_slot_input_dx",
  "cell_image_input_overlay": {
    "type": "panel",
    "size": [ 16, 16 ],
    "layer": 0,
    "controls": [
      { "item_renderer@$item_renderer_item": { "layer": 3 } },
      { "smelt_cell_slot@main_textures_dx.smelt_cell_slot": { } }
    ],
    "bindings": [
      {
        "binding_type": "view",
        "source_control_name": "$item_view_overlay",
        "source_property_name": "#toggle_state",
        "target_property_name": "#visible"
      }
    ]
  }
}
```

2. `vdx/ui_data/container/smelt_recipe_book/smelt_slot_output.uidx` (37 lines)
```json
{
  "namespace": "smelt_slot_output_dx",
  "cell_image_output_overlay": {
    "type": "panel",
    "size": [ 26, 26 ],
    "layer": 0,
    "controls": [
      { "item_renderer@$item_renderer_item": { "layer": 3 } },
      { "smelt_cell_slot_output@main_textures_dx.smelt_cell_slot_output": { } }
    ],
    "bindings": [
      {
        "binding_type": "view",
        "source_control_name": "$item_view_overlay",
        "source_property_name": "#toggle_state",
        "target_property_name": "#visible"
      }
    ]
  }
}
```

3. `vdx/ui_data/container/smelt_recipe_book/smelt_recipe_book.uidx` (37 lines)
```json
{
  "smelt_recipe_book_panel@common.root_panel": {
    "type": "input_panel",
    "layer": 1,
    "size": [ 147, 166 ],
    "$is_blast_furnace|default": false,
    "$is_smoker|default": false,
    "controls": [
      {
        "panel_content": {
          "type": "panel",
          "layer": 11,
          "controls": [
            { "header_text_panel@smelt_recipe_book_desktop_dx.header_text_panel": { } },
            { "filter_panel@smelt_recipe_book_filter_dx.filter_panel": { } },
            { "navigation_tabs@smelt_recipe_book_navigation_tabs_dx.navigation_tabs": { "layer": 1 } },
            { "recipe_item_pages@$recipe_book_pages_type": { "layer": 4 } }
          ]
        }
      }
    ]
  }
}
```

4. `vdx/ui_data/container/smelt_recipe_book/smelt_rendered_items.uidx` (45 lines)
```json
{
  "namespace": "cris_smelt_rendered_items",
  "item_renderer": {
    "type": "custom",
    "renderer": "inventory_item_renderer",
    "size": [ 16, 16 ],
    "$number_aux_index": 65536,
    "$number_data": 0,
    "property_bag": {
      "#item_id_aux": "($object_item_id * $number_aux_index + $number_data)"
    }
  },
  "item_image": {
    "type": "image",
    "texture": "$smelt_item_texture",
    "size": [ 16, 16 ]
  }
}
```

5. `vdx/ui_data/container/smelt_recipe_book/navigation_tabs.uidx` (29 lines)
```json
{
  "namespace": "smelt_recipe_book_navigation_tabs_dx",
  "stone_icon": {
    "type": "panel",
    "size": [ 16, 16 ],
    "controls": [
      { "0@cris_smelt_rendered_items.item_03_input_icon_00": { "ignored": "($is_blast_furnace)", "layer": 1 } },
      { "1@cris_smelt_rendered_items.item_60_input_icon_00": { "ignored": "(not $is_blast_furnace)", "layer": 3 } }
    ]
  }
}
```

## Modified Files

### Pause Screen
1. `vdx/ui_data/menu/pause.uidx`
```diff
+ "pause_text_label@label_dx.global_label": {
+   "shadow": true,
+   "text": "pauseScreen.gameIsPaused",
+   "color": [ 1.0, 1.0, 1.0],
+   "anchor_from": "bottom_right",
+   "anchor_to": "bottom_right",
+   "alpha": "@pause_dx.pause_text_label_animation_1",
+   "offset": [ -10, -6 ],
+   "layer": -20,
+   "bindings": [
+     {
+       "binding_name": "#pause_annoucement_visible",
+       "binding_name_override": "#visible",
+       "binding_type": "global"
+     }
+   ]
+ }

+ "pause_text_label_animation_1": {
+   "anim_type": "alpha",
+   "duration": 0.5,
+   "from": 1.0,
+   "to": 0.5,
+   "next": "@pause_dx.pause_text_label_animation_2"
+ }

+ "pause_text_label_animation_2": {
+   "anim_type": "alpha",
+   "easing": "in_expo",
+   "duration": 0.5,
+   "from": 0.5,
+   "to": 1.0,
+   "next": "@pause_dx.pause_text_label_animation_1"
+ }
```

2. `vdx/ui_data/menu_mixed/pause.uidx`
```diff
+ "pause_text_panel": {
+   "type": "panel",
+   "size": [ "100%cm", 32 ],
+   "controls": [
+     {
+       "background": {
+         "type": "image",
+         "size": [ "100%sm+22px", 24 ],
+         "alpha": 0.5,
+         "texture": "vdx/ui_textures/global/color_base",
+         "color": [ 0.0, 0.0, 0.0 ],
+         "layer": 1
+       }
+     },
+     {
+       "pause_text_label@label_dx.global_label": {
+         "shadow": true,
+         "text": "pauseScreen.gameIsPaused",
+         "color": [ 1.0, 1.0, 1.0],
+         "anchor_from": "center",
+         "anchor_to": "center",
+         "offset": [ 0, 0 ],
+         "layer": 4
+       }
+     }
+   ],
+   "bindings": [
+     {
+       "binding_name": "#pause_annoucement_visible",
+       "binding_name_override": "#visible",
+       "binding_type": "global"
+     }
+   ]
+ }
```

### Options
1. `vdx/ui_data/options/general.uidx`
```diff
- "graphics_mode_toggle": {
-   "type": "toggle",
-   "size": [ 310, 24 ]
- }
+ "graphics_mode_dropdown": {
+   "type": "dropdown",
+   "size": [ 310, 24 ],
+   "options": [
+     "options.graphics.fast",
+     "options.graphics.fancy",
+     "options.graphics.fabulous"
+   ]
+ }

+ "pause_toggle_panel": {
+   "type": "panel",
+   "size": [ "100%", 24 ],
+   "bindings": [
+     {
+       "binding_name": "#pause_toggle_enabled",
+       "binding_name_override": "#visible"
+     }
+   ],
+   "controls": [
+     {
+       "option_content_file_log@toggle_dx.option_toggle_list": {
+         "size": [ 310, 24 ],
+         "anchor_from": "top_middle",
+         "anchor_to": "top_middle",
+         "$option_label": "options.pauseHint",
+         "$option_binding_name": "#pause_option_toggle",
+         "$toggle_name": "pause_option_toggle"
+       }
+     }
+   ]
+ }
```

### HUD
1. `vdx/ui_data/hud/miscellaneous.uidx`
```diff
+ "number_of_days_played": {
+   "type": "panel",
+   "size": [ "100%", 9 ],
+   "controls": [
+     {
+       "bg": {
+         "type": "image",
+         "size": [ "100%c+1px", 9 ],
+         "texture": "vdx/ui_textures/hud/debug_text_bg",
+         "anchor_from": "top_left",
+         "anchor_to": "top_left",
+         "offset": [ 1, 0 ],
+         "controls": [
+           {
+             "text@label_dx.global_label": {
+               "size": [ "default", 10 ],
+               "offset": [ 1, 0 ],
+               "anchor_from": "top_left",
+               "anchor_to": "top_left",
+               "layer": 1,
+               "enable_profanity_filter": false,
+               "color": "$chat_text_color",
+               "text": "#text",
+               "shadow": false,
+               "bindings": [
+                 {
+                   "binding_name": "#number_of_days_played_text",
+                   "binding_name_override": "#text",
+                   "binding_condition": "always_when_visible",
+                   "binding_type": "global"
+                 }
+               ]
+             }
+           }
+         ]
+       }
+     }
+   ]
+ }
```

## Removed Files/Features

1. Play Screen
- Removed `ui/play_screen.json`
- Removed related UI components:
```diff
- "play_screen": {
-   "variables": [
-     {
-       "$screen_content": "play_dx.center_screen",
-       "$screen_bg_content": "play_dx.full_screen"
-     }
-   ]
- }
```

## Global Changes

### Version Updates
- Updated manifest.json:
```diff
- "min_engine_version": [1, 21, 60]
+ "min_engine_version": [1, 21, 70]
```

### Controller Support
- Added new tooltip controller textures:
```diff
+ "left_stick_directions": {
+   "type": "image",
+   "texture": "vdx/ui_textures/controller/left_stick_directions",
+   "size": [ 32, 32 ]
+ }

+ "dualsense_tooltip": {
+   "type": "image",
+   "texture": "vdx/ui_textures/controller/dualsense_tooltip",
+   "size": [ 32, 32 ]
+ }
```

## File Statistics
- Total new files: 5 (184 lines)
- Total modified files: 4 (156 lines changed)
- Total removed files: 1 (12 lines)
- Total line changes: 340 lines added, 12 lines removed

## Notes
- Recipe book changes are currently only available in Desktop UI
- Mixed UI and PvP UI recipe book support coming in future updates
- Pause announcement feature can be toggled in options
- All changes maintain backward compatibility with v1.21.70 