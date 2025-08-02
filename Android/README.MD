#To find the paths for apk files 
adb shell "find / -type f -name '*.apk' 2>/dev/null" > all_apk_paths.txt


#Pulling apk files

while read apk; do
  echo "Pulling $apk"
  adb pull "$apk" full_apk_dump/$(basename "$apk")
done < all_apk_paths.txt

#Check for crc

cd full_apk_dump

for file in *.apk; do
  unzip -v "$file" | awk '{print $8}' | grep -i '614c$' && echo "✅ Match found in: $file"
done
#to find the list of installed packages in android

adb list pm packages -f
#for third party apps
adb list pm packages -3
## path of the packages installed
adb shell pm path <packagename>
example: adb shell pm path com.malware.explorer

#crc
unzip -v <file.apk>

