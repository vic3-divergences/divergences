     example_progress_bar5 = {
        name = "PROGRESS_BAR_NAME1"
        desc = "PROGRESS_BAR_TEXT3" #This will be printed on the left side of the progress bar
       second_desc = "PROGRESS_BAR_TEXT3" #This will be printed on the right side of the progress bar
    
        start_value = 50
        min_value = 0
        max_value = 100
        
       # Use one of these types of progressbars:
        double_sided_gold = yes
       default_green = yes
        default_bad = yes
        default = yes
        double_sided_gold = yes
        double_sided_bad = yes
    
       These progress bar weekly/monthly/yearly progress updates executes before the weekly/monthly/yearly JE pulses
        weekly_progress = {
            add = {
                desc = "PROGRESS_BAR_ADD_WEEKLY_DESC2"
                value = 30
            }
        }
        monthly_progress = {
            add = {
                desc = "PROGRESS_BAR_ADD_MONTHLY_DESC1"
                if = {
                    limit = {
                        influence > 100
                    }
                    value = 3
                } 
            }
        }
        yearly_progress = {
        }
     }