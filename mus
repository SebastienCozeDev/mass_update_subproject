#!/bin/bash

# List of subprojects to update
subprojects=(
    "path/to/subproject1 commit_hash1"
    "path/to/subproject2 commit_hash2"
    "path/to/subproject3 commit_hash3"
)

# Browse the list of subprojects
for subproject in "${subprojects[@]}"; do
    path=$(echo "$subproject" | awk '{print $1}')
    commit=$(echo "$subproject" | awk '{print $2}')

    # Browse the list of subprojects and update them
    echo "Processing $path -> $commit"
    if [ -d "$path" ]; then
        cd "$path" || { echo "Failed to access $path"; exit 1; }
        git checkout "$commit" || { echo "Failed to checkout $commit in $path"; exit 1; }
        cd - > /dev/null || exit 1  # Return to the previous directory
    else
        echo "Directory $path does not exist. Skipping."
    fi
done

echo "Done."
