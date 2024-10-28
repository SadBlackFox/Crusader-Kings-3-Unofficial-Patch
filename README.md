[Unofficial patch] 

NOTE: Due to 1.13 Roads to power patch, A LOT of game files have changed, so instead of waiting a long time before seeing the patch I'll just make small update in order to get the patch out quicker.
For now the goal is to not make the game crash while still having the mod enabled !

common\activities\activity_types\feast.txt
> Add the support of iranian culture to display the mena background








-------------- LEGACY CHANGES DO NOT READ -------------- 

map_data/* => Fix the don river navigation issue & Ryazan county bordering the county of Tundokev
history\characters\*
    Turkish clean unintended char
    Sinhala clean unintended char
    irish
        Fix 1015 wrong father (was father = 131102 instead of father = 83117)
    Fix reference to the Flaithbertaig dynasty instead of the dynasty_house house_british_isles_flaithbertaig

gui
    shared
        cooltip: Fix some missing '=' sign
    activity_window_widgets
        tournament_contest_information: Fix extra ')'
        tournament_widget_types: Fix extra ')'
    event_windows
        character_event: Fix extra ')'
    texticons
        Replace attrition icon with the skull one
        New custom attrition while raiding icon (combine the skull and the torches)
    window_county_view: Add new code to give the possibility to revoke hostile holy orders from the barony UI
    hud: Fix extra ')'
    hud_notification_templates: Fix a size being 100%%
    interaction_declare_war: Put the max width of the text at 500 instead of 350 for the holy war warning
    interaction_interfere_in_war_notification: Add a missing }
    interaction_templates: Fix extra ')'
    map_icon_layer: Fix extra ')'
    multiplayer_types: Fix some margins missing their '=' assignment
    window_activity_locale: Fix extra ')'
    window_barbershop: Fix extra ')'
    window_county_view: Fix an extra ';' and replace one in an align command (using a | as it should)
    window_create_accolade: Fix extra ')'
    window_languages: Fix extra ')'
    window_menatarms: Fix extra ')'

gfx
    map\map_object_data: New files for the map_data modifications
    court_scene\00_default_roles: Fix relation guardian being improperly checked
    models
        artifacts\ep2\ep2_western_crown_01_a Add a missing '}'
        buildings/holdings/india_temple_christian_01/building_indian_temple_christian_01.asset Fix extra ')'
        debug/test_objects.asset  Fix extra ';'
        portraits/attachments
            female_headgear
                religious/steppe/high_01/female_headgear_religious_steppe_high_01.asset Add missings '}'
                special/ep2_byzantine/wedding/f_headgear_spec_ep2_byzantine_wedding.asset Add missings '}'
                special/ep2_mena/wedding/f_headgear_spec_ep2_mena_wedding.asset Add missings '}'
            male_headgears
                secular/byzantine/high_nobility_01/male_headgear_secular_byzantine_high_nobility_01.asset Add missings '}'
                secular/dde_hre/common_01/male_headgear_secular_dde_hre_common_01.asset Add missings '}'
                secular/ep1/mena_royalty_02/male_headgear_secular_ep1_mena_royalty_02.asset Add a missing '}'
    portraits/portrait_modifiers
        00_custom_legwear.txt Add a missing '}'
        00_custom_headgear.txt Add the stealth headgear for mean & western in the barbershop
        00_custom_clothes.txt Add the stealth torso for mean & western in the barbershop
        02_all_historical_characters.txt Change Matilda cloak to f_cloaks_sec_ep2_western_era1_nob_01_hi for naming consistancy
        05_cloaks_situational.txt Add a trigger to remove the cloak if the char should be in "stealth mode" for ep2_western_travel_cloak & ep2_mena_travel_cloak & ep1_adventurer_cloak

common
    decisions
        99_unop_override_decisions
            Override specific stress_loss_flagellant_decision to show if you have a faith with the doctrine self_mutilation_active and added that you'll gain minor piety

    important_actions
        00_personal_actions: Make the ransom decision take into account the fp1_pillage_legacy_3 for increase ransom

    religion
        doctrines
            00_core_tenets
                Fix tenet_alexandrian_catechism not showing because needing both christianity & islam tag
                Fix tenet_exaltation_of_pain not showing up
                Fix tenet_communal_possessions not showing up

    scripted_effects
        00_interaction_effects
            torturer_interaction_recipient_effect: Take the faith doctrine reduced_stress_from_torture into account so the char who is tortured have stress reduction



events
    activities
        pilgrimage_activity
            pilgrimage.6800: Fix option E setting the wrong friendship
    stress_events
        stress_trait_coping_decisions_events
            stress_trait_coping_decisions.3501: Now add minor piety if you have the faith doctrine self_mutilation_active 
