﻿	catalyst_example = {
		# Which diplomatic_catalyst_category does this catalyst belong to
		category = cc_example 
	
		# Data for creating lobbies as a result of this catalyst
		political_lobby_creation = {
			# Trigger for whether to evaluate the script values below at all
			# Mostly used to save on performance by avoiding costly calculations when not needed, as <= 0 lobby script value has the same effect
			# Scopes:
			# root = the country the catalyst was triggered for
			# scope:target_country = the country the catayst was triggered by
			trigger = {}
		
			# Script values for chance to try and create one or more lobby types
			# Same scopes as trigger	
			lobby_example_1 = {}
			lobby_example_2 = {}
		}
	
		# Data for changing AI strategic desires as a result of this catalyst
		ai_country_goal_recalculation = {
			# Which directions the catalyst is allowed to change the AI's strategic desire, must be set
			# all = any valid strategic desire
			# more_friendly = only towards valid friendlier strategic desires (for instance antagonize -> none, none -> befriend or antagonize -> befriend)
			# more_hostile = only towards valid more hostile strategic desires (for instance none -> antagonize, befriend -> none or befriend -> antagonize)
			# only_friendly = only to a friendly valid strategic desire (for instance 'befriend') - no effect if current strategic desire is already friendly & valid
			# only_hostile = only to a hostile valid strategic desire (for instance 'antagonize') - no effect if current strategic desire is already hostile & valid
			# only_neutral = only to a neutral valid strategic desire (for instance 'none') - no effect if current strategic desire is already neutral & valid
			type = all/more_friendly/more_hostile/only_friendly/only_hostile/only_neutral
		
			# Trigger for whether to evaluate the script value below at all
			# Mostly used to save on performance by avoiding costly calculations when not needed, as <= 0 chance has the same effect
			# Scopes:
			# root = the country the catalyst was triggered for
			# scope:target_country = the country the catayst was triggered by
			trigger = {}
		
			# Script value for chance to recalculate the AI's strategic desire (0 = 0%, 1 = 100%)
			# Same scopes as trigger
			chance = {}
		}
	
		# Effect that is executed when catalyst occurs
		# Scopes:
		# root = the country the catalyst was triggered for
		# scope:target_country = the country the catayst was triggered by
		effect = {}
	}
