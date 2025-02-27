# Automate-image-removal

import os
import shutil

# Set the folder path
folder_path = "path/to/your/folder"
output_folder = "path/to/save/remaining_images"

# Ensure output folder exists
os.makedirs(output_folder, exist_ok=True)

# Iterate through files in the folder
for filename in os.listdir(folder_path):
    # Check if the filename ends with _1 to _22 before the file extension
    if any(filename.endswith(f"_{i}.jpg") or filename.endswith(f"_{i}.png") or filename.endswith(f"_{i}.jpeg") for i in range(1, 23)):
        continue  # Skip these files

    # Copy the remaining files to the output folder
    shutil.copy(os.path.join(folder_path, filename), os.path.join(output_folder, filename))

print("Filtered images saved successfully!")
