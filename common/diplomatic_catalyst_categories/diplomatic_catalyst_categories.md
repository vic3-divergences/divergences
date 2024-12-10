	cc_example = {
		# If a lobby has a formation reason set, this can affect its join weights (armed forces being more inclined towards a lobby created for mutual defense, etc)
		# Does not need to be set, lobbies can be formed without an explicit reason
		lobby_formation_reason = diplomacy/defense/ideology/funded/aggression/religion/technology/economy/none
	
		# How long is the catalyst stored in the gamestate before being removed
		# Must be greater than 0 days
		duration = {
			years = 5
		}
	
		# Optional cooldown before a catalyst of the same category can attempt to create a lobby or recalc secret goals
		# Cannot be longer than duration
		catalyst_effect_cooldown = {
			years = 1
		}
	}
