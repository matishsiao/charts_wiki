**version: 1.1 / stability: 2 (rather stable)**

`Feature` or `featureset` means a part of chart's functionality. There are simple (atomic) and complex (composite) features. Composite feature consists of simple features. Disabling composite feature makes all of its simple parts to be disabled. Supported features are listed below.

###header_widget
It is a composite feature. it is **on** by default. Simple features included here:

* header_symbol_search
* header_resolutions
* header_chart_type
* header_settings
* header_indicators
* header_compare
* header_undo_redo
* header_screenshot
* header_fullscreen_button
* header_saveload

###context_menus
It is a composite feature. it is **on** by default. Simple features included here:
* pane_context_menu
* scales_context_menu
* legend_context_menu

###Standalone Features Not Belonging To Composite Ones

Features switched **on** by default:

* left_toolbar
* control_bar
* timeframes_toolbar
* edit_buttons_in_legend
* use_localstorage_for_settings
* volume_force_overlay
* create_volume_indicator_by_default
* right_bar_stays_on_scroll

Features switched **off** by default:

* charting_library_debug_mode
* narrow_chart_enabled
* trading_options
* move_logo_to_main_pane
