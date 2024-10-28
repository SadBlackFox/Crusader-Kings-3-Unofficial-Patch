[Unofficial patch] 

NOTE: Due to 1.13 Roads to power patch, A LOT of game files have changed, so instead of waiting a long time before seeing the patch I'll just make small update in order to get the patch out quicker.
For now the goal is to not make the game crash while still having the mod enabled !

Unfixable bugs from my side:
- Royal court food amenity bonus given to characters in your dungeon

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

    character_interactions
        00_scheme_interactions.txt
            > Fix abduct interaction not checking the domicile building


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
    scheme_events
        laamp_base_contract_scheme_events.txt
            > Add an exists check to prevent many errors in the log file
    siege_events.txt
        > Revert a bug caused by 1.13 patch preventing you to capture people after a siege    

gfx
    map\map_object_data: New files for the map_data modifications

map_data/* => Fix the don river navigation issue & Ryazan county bordering the county of Tundokev