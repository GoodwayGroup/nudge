Nudge is used to manage OS X Updates.

Adopted from the instructions here: https://robin.lauren.fi/posts/deploying-nudge-customised

Nudge Repo: https://github.com/macadmins/nudge
Munki Repo: https://github.com/munki/munki-pkg (Munki is needed to update and redeploy the Nudge package file)

All updates files have been uploaded to this repo.

The .plist file defines the schedule run time, which is currently every weekday at 8 AM and it points to the JSON file stored on GitHub.
This allows us to the update the min required OS X version without having to redploy Nudge

1. Download Nudge and clone the Munki Repo
2. Create a working directory and open a Terminal window to the directory
3. Execute `~/git/munki/munki-pkg/munkipkg --import ~/Downloads/Nudge_Suite-1.1.11.81465.pkg Nudge_Suite-1.1.11.81465`, replacing paths and version numbers as appropriate.
4. To update the scheduled run-time or link to a new JSON config file modify this file `payload/Library/LaunchAgents/com.github.macadmins.Nudge.plist` located within the .pkg file, example `/build/Nudge_Suite-1.1.16.81564.pkg/payload/Library/LaunchAgents`
5. Once complete, execute `~/git/munki/munki-pkg/munkipkg --build Nudge_Suite-1.1.11.81465`, replacing paths and version numbers as appropriate
6. The completed pkg which should be uploaded to Kandji will be located within the `build` folder within the pkg folder, example `/build/Nudge_Suite-1.1.16.81564.pkg/build`
7. To update the min version of any UI elements modify `com.github.macadmins.Nudge.json` in this repo, Nudge will automatically pull it down on run time.