# Reference
```
your_status_key = {
    threshold = 0
    base_migration_desire = 50
	war_exhaustion_impact_own_side / war_exhaustion_impact_other_side = 2.0
}
```

# Requirements

At least one valid acceptance status needs to be scripted for the game to
function.

Every status must have a unique threshold; i.e. no two status must have the
same threshold.

The threshold of every status must be >= MIN_ACCEPTANCE_VALUE
and <= MAX_ACCEPTANCE_VALUE (those are defines).

The threshold for one of the statuses must match MIN_ACCEPTANCE_VALUE. The
status with a threshold of MIN_ACCEPTANCE_STATUS is the first status
(ordinally, it does not have to be the first in script order).

# Behavior

Acceptance statuses whose threshold falls outside the minimum and maximum
bounds will be ignored (an error will be logged in the error log).

The order in which the statuses are scripted matters partially. The in-game
internal sorting of the statuses is determined by the order of their
thresholds, not the order in which they are scripted.

However, if two statuses share the same threshold, only the first one is
considered, and all the following statuses (in script order) that share the
same threshold will be ignored.

The threshold of a status is the acceptance value at which a pop is considered
to start being part of that status (inclusive). In other words, a status'
threshold is the minimum acceptance value necessary to be part of that racket.

The maximum acceptance value for the racket is not scripted, but is derived
from the threshold of the next racket. This is done to avoid accidental gaps
between statuses.

The maximum acceptance value for the last status is MAX_ACCEPTANCE_VALUE.

Once statuses are parsed and filtered, the remaining valid ones are internally
sorted and given an ordinal number from 1 to N.

# Example

```
status_1 = {
    threshold = 95
}

status_2 = {
    threshold = 50
}

status_nonunique = {
    threshold = 50
}

status_3 = {
    threshold = 140
}

MIN_ACCEPTANCE_VALUE = 50
MAX_ACCEPTANCE_VALUE = 130
```

In the above example, an acceptance value between 50 and 94 (inclusive) would
make a pop fall within `status_2`, while a value of 95 to 130 (inclusive) would
make the pop fall within `status_1`.

`status_nonunique` is ignored because it shares a threshold with
`status_2`, but `status_2` comes first in script order.

`status_3` is ignored because its threshold is > MAX_ACCEPTANCE_VALUE.

`status_1` would have an ordinal value of 2, `status_2` would have an
ordinal value of 1. It does not matter that `status_1` is scripted first,
it has an ordinal of 2 because there are 2 statuses, one valid for values
50 - 94 and one valid for values 95 - 130, and `status_1` is the latter,
regardless of the fact that it's called `status_1`.

# List of scriptable keys

## threshold
Is the minimum (inclusive) acceptance value that determines if a pop falls
within this status

## base_migration_desire
Every pop falling in this status will have this as its base migration desire.
A higher migration desire makes pop more likely to be selected from migration,
but only if those pops are allowed to do so.

Whether a pop is allowed to migrate is dictated by the migration restrictiveness
modifier, which is determined by laws.

## war_exhaustion_impact_own_side
## war_exhaustion_impact_other_side
When someone dies in a war, due to battles or attrition, we keep track of their culture.
Based on a country's Acceptance of that culture, they will gain War Exhaustion each week 
relative to this factor compared to the number of total men mobilized in this war.
For example, if 300K individuals with the same acceptance status in a given country have
died  in the war compared to 500K currently mobilized, 140K on their side and 160K on
the other, and these values are set to 2.0 vs 0.5 respectively, a country with this level
of acceptance will gain 
140K/500K * 2 + 160K/500K * 0.5 = 0.56 + 0.16 = 0.72 War Exhaustion on a weekly basis