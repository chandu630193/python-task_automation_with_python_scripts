import os
import shutil


def organize_jpg_files(source_dir: str, destination_dir: str):
    # Ensure destination folder exists
    os.makedirs(destination_dir, exist_ok=True)

    # Check if source directory exists
    if not os.path.exists(source_dir):
        print(f"Error: Source directory '{source_dir}' does not exist.")
        return

    moved_count = 0

    # Iterate through all files in the source directory
    for filename in os.listdir(source_dir):
        source_path = os.path.join(source_dir, filename)

        # Check if it is a file and ends with .jpg or .jpeg
        if os.path.isfile(source_path) and filename.lower().endswith(
            (".jpg", ".jpeg")
        ):
            dest_path = os.path.join(destination_dir, filename)
            shutil.move(source_path, dest_path)
            print(f"Moved: {filename}")
            moved_count += 1

    print(f"\nTask completed. Total JPG files moved: {moved_count}")


if __name__ == "__main__":
    SOURCE = "path/to/source_folder"
    DESTINATION = "path/to/jpg_folder"
    organize_jpg_files(SOURCE, DESTINATION)
