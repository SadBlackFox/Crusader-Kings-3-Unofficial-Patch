[Unofficial patch] 

NOTE: Due to 1.13 Roads to power patch, A LOT of game files have changed, so instead of waiting a long time before seeing the patch I'll just make small update in order to get the patch out quicker.
For now the goal is to not make the game crash while still having the mod enabled !

Unfixable bugs from my side:
- Royal court food amenity bonus given to characters in your dungeon
- The Barber's Tent disease resistances is not applying to all camp followers

Here is the list of ported fixes (or new ones) at the moment:

common
    activities
        activity_types
            feast.txt
                > Add the support of iranian culture to display the mena background
            gruesome_festival.txt
                > Changed the cost for the option gruesome_festival_sacrifice_animals_magnificent_poser (to be shown / to be refunded) to gruesome_festival_option_medium
            pilgrimage.txt
                > Add the iranian_culture_group with the mena_culture_group to display a better background
    
    court_positions
        types
            00_court_positions.txt
                > Fix court gardener recruitment using court_artificer_validity_trigger
                > Fix 2 court scholar aptitude bonus

    character_interactions
        00_scheme_interactions.txt
            > Fix abduct interaction not checking the domicile building

    customizable_localization
        05_bp2_custom_loc.txt
            > Fix RockStoryName missing roxanne & barney entries leading to blank text in events

    domiciles
        buildings
            00_estate_buildings.txt
                > Fix estate graphics defaulting to byzantine skin if you have the iranian graphic group
                > Fix wrong label for the living quarter gold reduction
                > Fix incorrect file reference for the byzantine mask
                > Fix market_06 intersectionmask_texture path

    important_actions
        00_personal_actions.txt
            > Add an action to display the correct amount of gold you can ransom someone if you have Practiced Kidnappers

    schemes
        scheme_types
            abduct_scheme.txt
                > Fix wrong domicile parameter check

    scripted_effects
        00_holy_order_effects.txt
            > Fix the executioner recruitment
        00_prison_effects.txt
            > Fix the mass ransom when you have Practiced Kidnappers

    scripted_triggers
        00_court_position_triggers.txt
            > Add some missing exclusive court/officer position inside court_position_does_not_already_have_a_job_trigger
        20_health_triggers.txt
            > Fix has_high_health_penalty_disease_type_trigger & has_low_health_penalty_disease_type_trigger for elderly/child characters who have consumption or measles 

events
    dlc
        ce1
            legend_spread_events_nick.txt
                > Fix legend_spread_events.5305 that could potentially select a ruler that is already spreading your legend as a valid legend promoter
                > Fix legend_spread_events.5310 that could potentially select a ruler that is already spreading your legend as a valid legend promoter
            legend_spread_events_8.txt
                > Fix legend_spread_events.8122 by ensuring saved ruler is still the actual ruler once you arrive on the land
                > 

    scheme_events
        laamp_base_contract_scheme_events.txt
            > Add an exists check to prevent many errors in the log file
            > Fix a wrong scope used for the gold received for the employer in laamp_base_contract_schemes.2002
        scheme_critical_moments_events.txt
            > Fix scheme_critical_moments.0001 incorrect scheme type selection
            > Misc cleanup of scheme_critical_moments.1174 wild if
            > Fix scheme_critical_moments.8031 missing the mark building condition
            > Fix raid_estate_success_effect missing the market flag

    siege_events.txt
        > Revert a bug caused by 1.13 patch preventing you to capture people after a siege
        > Fix master of spoils camp officer not increasing the chance to get an artifact after a siege

    trait_specific_events
        trait_specific_events.txt
            > trait_specific.1010 & trait_specific.2002 & trait_specific.3002 have been harmonized to enable the genetic bad trait (if you have one) instead of adding the non-genetic one
            > Fix trait_specific.8501 out of order scope definition & duplicate effect usage

    travel_events
        travel_events_james.txt
            > Prevent travel_events.4013 to add a friend relation if you already have one
            > Fix travel_events.4033 memory if you burn the witch
            > Fix travel_events.4036 not defining required artifact variables that cause some script errors later

gfx
    map\map_object_data: New files for the map_data modifications

gui
    hud.gui
        > Allow the tax collector button to be show as soon as you have a taxable vassal

map_data/* => Fix the don river navigation issue & Ryazan county bordering the county of Tundokev