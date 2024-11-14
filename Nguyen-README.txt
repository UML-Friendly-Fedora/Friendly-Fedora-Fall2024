I analyzed the compose_tracker.py file this week. I looked through each function
and made sure to understand what was going on. The __init__ function initializes
the Consumer inside the Consumer class. The get_supporting_text function analyzes log
lines to find relevant task IDs. This function mentions koji task and I would like to
know more of what koji task are. The get_maintainers fetches from a TOML and parses it
and loads it into maintainers_info. Its looking for regex patterns that match with
variant, arches, and subvariants. This includes architecture specifications and 
variants like x86 or x64 and so on. Each match is stored in matching_list. The
__call__ processes each message received from the consumer and extracts the message
and is catching for errors. The process function is logging the status of each compose
and retrives the parsed files. It also calculates the log time.