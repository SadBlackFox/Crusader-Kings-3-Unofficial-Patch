# [Unofficial patch] 8.0.8

NOTE: Due to 1.13 Roads to power patch, A LOT of game files have changed, so instead of waiting a long time before seeing the patch I'll just make small update in order to get the patch out quicker.
For now the goal is to not make the game crash while still having the mod enabled !

---

### [TL;DR] AKA: What change ?
 - error.log file will eat way less disk space
 - Some events now correctly apply the effects
 - Less events with '.' as text options
 - Less spouse cheating
 - Dynamic culture cost / reward for dynasty prestige is now working
 - Marshall train commander task can now train more the once the same knight
 - Many other things, but check the in-depth changelog below

---

### Unfixable bugs from my side:
- Royal court food amenity bonus given to characters in your dungeon
- The Barber's Tent disease resistances is not applying to all camp followers
- Forder trait does not negate river crossing penalties
- The typo in the excerpt on the table being 'ma tyly' instead of maȝtyly

---

### Here is the list of ported fixes (or new ones) at the moment:
```
common
    activities
        activity_types
            feast.txt
                > Add the support of iranian culture to display the mena background
            gruesome_festival.txt
                > Changed the cost for the option gruesome_festival_sacrifice_animals_magnificent_poser (to be shown / to be refunded) to gruesome_festival_option_medium
            hunt.txt
                > Add an event in case the host dies but not from a hunt event            
            pilgrimage.txt
                > Add the iranian_culture_group with the mena_culture_group to display a better background
        activity_system_events.txt
            > Flag activity_system.0091 & activity_system.0092 as orphan as they are replace with an in-house event
        intents
            shared_intents.txt
                > Fix the target intent invalidation event not firing
            wedding_intents.txt
                > Fix the target intent invalidation event not firing
    buildings
        00_duchy_capital_buildings.txt
            > Re-introduced Charnel Grounds that got wrongfully removed in the 1.13 patch

    court_positions
        tasks
            00_court_positions_tasks.txt
                > Will now show that the charioteer can have a task and what is the requirement
        types
            00_court_positions.txt
                > Fix court gardener recruitment using court_artificer_validity_trigger
                > Fix 2 court scholar aptitude bonus
                > Add all missing salary increase check
                > Add the missing aptitude bonus check for the gardener & chief_eunuch & champion given by court.8311

    character_interactions
        00_scheme_interactions.txt
            > Fix abduct interaction not checking the domicile building
        06_ep3_interactions.txt
            > Fix AI sending child with the offer_eunuch_interaction
        

    customizable_localization
        00_relations.txt
            > Fix some triggers to ensure you won't be calling other char with court position as being your own
        05_bp2_custom_loc.txt
            > Fix RockStoryName missing roxanne & barney entries leading to blank text in events

    decisions
        dlc_decisions
            03_fp2_decisions.txt
                > Fix HoF counting as a potential independant ruler for Iberia struggle detente ending (only it it's the char primary title)
        00_major_decisions_iberia_north_africa.txt
            > Fix reversed text in mozarabic_break_with_rome_decision (righteous & fundamentalist)

    domiciles
        buildings
            00_estate_buildings.txt
                > Fix estate graphics defaulting to byzantine skin if you have the iranian graphic group
                > Fix wrong label for the living quarter gold reduction
                > Fix incorrect file reference for the byzantine mask
                > Fix market_06 intersectionmask_texture path

    genes
        05_genes_special_accessories_clothes.txt
            > Add missing female_clothes_religious_buddhist_devoted_01
            > Fix female_clothes_religious_buddhist_devoted_01 being referenced as female_clothes_religious_hindu_devoted_01 

    important_actions
        00_personal_actions.txt
            > Add an action to display the correct amount of gold you can ransom someone if you have Practiced Kidnappers

    on_action
        childhood_on_actions.txt
            > Add 2 events fallback in case of education invalidation (yes it still happen for AI)
        province_on_actions.txt
            > Fix building built by norman not increasing the pacification for the harrying_of_the_north (but restrict it to Norman being in England)
        ruler_designer.txt
            > Change the government of newly created character depending of the faith you set

    schemes
        scheme_types
            abduct_scheme.txt
                > Fix wrong domicile parameter check

    scripted_effects
        00_holy_order_effects.txt
            > Fix the executioner recruitment
        00_prison_effects.txt
            > Fix the mass ransom when you have Practiced Kidnappers
        00_laamp_effects.txt
            > Fix laamp_contract_grab_suitable_rival_for_disposal_effect using an undefined scope
        07_dlc_ep3_scripted_effects.txt
            > Fix laamp_as_mercenary_payout_effect that was putting all mercenaries in the same list instead of seperating them. That lead to the wrong outcome letter event after a war
        00_decisions_effects.txt
            > Fix launch_hungarian_migration_scripted_effect using twice a limit instead of an alternative_limit 

    scripted_triggers
        00_court_position_triggers.txt
            > Add some missing exclusive court/officer position inside court_position_does_not_already_have_a_job_trigger
            > Change can_appoint_char_to_court_position to also check if the employer is actaully employing someone
        20_health_triggers.txt
            > Fix has_high_health_penalty_disease_type_trigger & has_low_health_penalty_disease_type_trigger for elderly/child characters who have consumption or measles 
        00_scheme_triggers.txt
            > Fix agent_valid_to_be_discovered_by_spymaster using the wrong scope target instead of target_character

    script_values
        00_basic_values.txt
            > Rework scale_dynasty_prestige_by_era to handle if a character is given
            > Fix gift_artifact_opinion checking raw durability instead of % of left durability
        10_health_values.txt
            > Fix the variable value for under/overweight for script using it
        07_ep3_values.txt
            > Fix ep3_laamp_chance_score_value that gave way more score than intended for char to decide if they should be an adventurer

    task_contracts
        laamp_base_contracts.txt
            > Add some missing scope saving to prevent some errors (sadly still have work to do there)

events
    activities
        chariot_race_activity
            chariot_race_ongoing_events.txt
                > Fix chariot_race.3030 to use the proper trigger & effect to affect a charioteer
                > Fix chariot_race.3050 
            chariot_ongoing_events_jp.txt
                > Prevent the HoF to be selected as a valid target for chariot_race_ongoing_jp.0201
        hold_court_activity
            hold_court_events_general.txt
                > Fix hold_court_8090_can_move_trigger that could select character that are married to landed ruler
                > Rework hold_court.8090 to ensure the logic of court position (replace/free sport/bad sport) is always respected.
                > Fix hold_court.6120 by re-introducing some change made in 1.13 that now prevent the tooltip of the option to display the effect properly
                > Fix hold_court.6130 same as above

    councillor_task_events
        marshal_task_events.txt
            > Add more check to marshal_task_0302_commander_trigger to avoid conflicts with vassal.2701 & vassal.2702
            > Fix marshal_task.0302 using an after block (that does not work in hidden events)
            > Add more checks to marshal_task_2101_teacher_trigger to ensure the selected commander is available and healthy
            > Add more check to marshal_task_2101_commander_trigger to avoid conflicts with vassal.2701 & vassal.2702 
            > Rework marshal_task.2101 to ensure the duo mentor/student is correct, also the event was using an after block (that does not work in hidden events)

    court_events_general
        court_events_general.txt
            > Fix all missing variable to court.3031 that broke the event text

    dlc
        ce1
            legend_spread_events_nick.txt
                > Fix legend_spread_events.5305 that could potentially select a ruler that is already spreading your legend as a valid legend promoter
                > Fix legend_spread_events.5310 that could potentially select a ruler that is already spreading your legend as a valid legend promoter
            legend_spread_events_8.txt
                > Fix legend_spread_events.8122 by ensuring saved ruler is still the actual ruler once you arrive on the land
                > Fix ep3_laamp_flavour_ewan.3031 claim ordering
                > Fix legend_spread_events.8160 looking for legend chapter that does not exists
            epidemic_events.txt
                > Ensure all legitimacy change use the effect that ensure the char is using legitimacy (reduce logged errors)
                > Ensure events that infect you use the proper effect to ensure that you are not immune to the disease and also will launch the physician treatment event & later recovery
        
        ep3
            ep3_laamp_events.txt
                > Fix ep3_laamps.5040 wrong scope use to give a nickname to the merchant
                > Fix ep3_laamps.7003 not registering target location for use in ep3_laamps.7004
                > Fix ep3_laamps.7004
                    > Not making you vassal of the holder
                    > Not giving you the correct government than what was displayed in the tooltip
                    > Flooding the event option with a list of nothing happen
                    > Changing the name of all counties of the holder to english ones instead of the one the holder sold you 
            ep3_laamp_decision_event.txt
                > The first time you enter the barracks as an adventurer, the 6th rule of the fight club is now enforced
            ep3_laamp_flavour_ewan_events.txt
                > Fix ep3_laamp_flavour_ewan.1111 sadistic option stress that was reversed
                > Fix ep3_laamp_flavour_ewan.3041 character creation that used the wrong scope for culture & faith
                > Fix ep3_laamp_flavour_ewan.9511 character creation age value
                > Fix ep3_laamp_flavour_ewan.9512 wrong animation
                > Fix ep3_laamp_flavour_ewan_9521_change_visitor_culture_effect culture comparison
                > Fix ep3_laamp_flavour_ewan_9521_apply_ethos_skill_bonuses_effect not being scope to the scope:visitor in some places
                > Fix ep3_laamp_flavour_ewan_9522_change_visitor_faith_effect faith comparison
            ep3_story_cycle_harrying_of_the_north_events
                > Prevent vassal child to be selected as valid target for event ep3_story_cycle_harrying.3021

        fp2
            fp2_struggle_events.txt
                > Fix fp2_struggle.0003 & fp2_struggle.0004 duplicate top scope (the none one)
                > Fix fp2_struggle.0501 option A sound effect
                > Fix fp2_struggle.0900, fp2_struggle.0910, 
                > Fix fp2_struggle.1001 missing alternative_limit that could break the event
                > Fix fp2_struggle.1010 not ensuring the building with blacksmiths_01 (or higher was in Iberia)
                > Fix fp2_struggle.1020 logic where AI could select themselves multiple times as event characters
                > Fix fp2_struggle.2005 wrongly overriding 2005_scoped_steward
                > Fix fp2_struggle.2006 by ensuring your chaplain is not the holder
                > Fix fp2_struggle.2007 refund cost that can be higher or lower (was base in your income instead of what you actually paid)
                > Fix fp2_struggle.2009 by ensuring it cannot select a ruler that is at sea
                > Rework fp2_struggle.2015 logic to select the vassal by order of opinion
                > Add a fallback in case fp2_struggle.2021 fire while you are at sea
                > Prevent fp2_struggle.3021 from selecting your spouse or heir

    scheme_events
        laamp_base_contract_scheme_events.txt
            > Add an exists check to prevent many errors in the log file
            > Fix a wrong scope used for the gold received for the employer in laamp_base_contract_schemes.2002
        
        laamp_base_learning_contract_events.txt
            > Fix laamp_base_learning_contract_events.4001 clearing the wrong flag preventing the language option being selectable after the first event
            > Fix 4100_save_background_effect using the wrong scope to check for season
        
        scheme_critical_moments_events.txt
            > Fix scheme_critical_moments.0001 incorrect scheme type selection
            > Misc cleanup of scheme_critical_moments.1174 wild if
            > Fix scheme_critical_moments.8031 missing the mark building condition
            > Fix raid_estate_success_effect missing the market flag
        seduce_scheme
            seduce_ongoing_events.txt
                > Fix seduce_ongoing.1101 checking your char instead of the target for gift
                > Fix seduce_ongoing.1202 event desc missing a part
            
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
        travel_start_events.txt
            > Prevent travel_start_event.1070 to log error when you don't have a caravan master

    yearly_events
        court_yearly_events.txt
            > Fix event_0101_spawn_criminal_effect scoping issue to check for clergy gender
        yearly_events.txt
            > Add some check to ensure cheating likeliness
        yearly_events_2.txt
            > Add some check to ensure cheating likeliness in yearly.1001 & yearly.1010 & yearly.1060 / yearly_1060_possible_flirt_trigger & yearly_1060_joker_trigger 
        yearly_events_3.txt
            > Add some check to ensure cheating likeliness
        yearly_events_5.txt
            > Fix yearly.5020 reversed mentor/student relation setup

gfx
    map\map_object_data: New files for the map_data modifications

    portraits
        portrait_modifiers
            00_custom_clothes.txt
                > Add Western & Mena clothes.
                > Fix template western_royalty_clothes name (was: western_royal_clothes)
                > Fix religious_jain_high_clothes name (was: religious_jain_devoted_clothes)
            00_custom_headgear.txt
                > Add Western & Mena hood.
                > Fix ep3_byzantine_era1_commoner name (was: ep3_byzantine_era1_common)
                > Comment a duplicated entry for fp4_western_era2_veils
                > Comment a non existing entry for ep3_byzantine_era2_common
            05_cloaks_situational.txt
                > Force the cloak to be hidden in some cases

gui
    shared
        cooltip.gui
            > Fix a missing '=' sign

    hud.gui
        > Allow the tax collector button to be show as soon as you have a taxable vassal

map_data/* => Fix the don river navigation issue & Ryazan county bordering the county of Tundokev
```