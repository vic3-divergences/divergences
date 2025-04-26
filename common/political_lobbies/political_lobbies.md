﻿	lobby_example = {
		# Lobby category - this affects which type of country they target (foreign or self) and their general stance towards that country
		category = foreign_pro_country/foreign_anti_country/foreign

		# Icon
		texture = "gfx/interface/icons/political_lobby_icons/lobby_pro.dds" 

		# Trigger that must evaluate true to create a lobby
		# root = the interest group looking to join/leave
		# scope:country = the country the lobby belongs to
		# scope:target_country = the country the lobby is targeting (same as scope:country for domestic lobbies)
		can_create = {}
	
		# Effect that is fired after a lobby is created
		# Scopes:
		# root = the interest group looking to join/leave
		# scope:country = the country the lobby belongs to
		# scope:target_country = the country the lobby is targeting (same as scope:country for domestic lobbies)
		# scope:political_lobby = the lobby
		on_created = {}
	
		# Conditions that must evaluate true to maintain a lobby
		# Any number of requirements can be scripted in
		# Scopes:
		# root = the interest group looking to join/leave
		# scope:country = the country the lobby belongs to
		# scope:target_country = the country the lobby is targeting (same as scope:country for domestic lobbies)
		# scope:political_lobby = the lobby. Not set if evaluating a potential lobby that could be created.
		requirement_to_maintain = {
			trigger = {} # Trigger that must be satsified for the lobby to not disband or change type	
			on_failed = {} # Effect that is executed if a requirement to maintain fails
			swap_type_on_failed = <lobby type key> # If this is set, the lobby attempts to change into a lobby of the specified type instead of being disbanded
		}	
	
		# Lists of appeasement_factors, pro and anti
		# Appeasement factors not marked as is_always_usable must be set here to be usable for the lobby
		# Cannot contain appeasement factors marked as is_always_usable
		appeasement_factors_pro = {}
		appeasement_factors_anti = {}
	
		# Trigger for whether an IG can join the lobby (not checked for IGs that are already members)
		# Scopes:
		# root = the interest group looking to join
		available_for_interest_group = {}
	
		# Script value for how interested an IG is in joining a lobby
		# Scopes:
		# root = the interest group looking to join/leave
		# scope:country = the country the lobby belongs to
		# scope:target_country = the country the lobby is targeting (same as scope:country for domestic lobbies)
		# scope:political_lobby = the lobby. Not set if evaluating a potential lobby that could be created.
		join_weight = {}
	}
