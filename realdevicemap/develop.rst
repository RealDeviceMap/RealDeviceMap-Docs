###########################
Develop
###########################
.. include:: ../../formatting.rst
.. contents::
  :local:

Install Requirements
----------------------------
- Xcode 9+: From App Store
- MysqlClient 5.7: ``brew install mysql@5.7 && brew link mysql@5.7 --force``
- ImageMagick: ``brew install imagemagick``


Generate the Xcode Project
----------------------------
- Run this in the RDM folder: ``swift package generate-xcodeproj``


Configure Xcode Project
----------------------------
- Open the newly generated ``.xcodeproj`` file.
- Open Product -> Scheme -> Edit Scheme...
- Select Run -> Arguments
- Add this enviroment variable: ``PROJECT_DIR=${PROJECT_DIR}``
- Add other enviroment variables like `DB_PASSWORD` etc.
- Click Close
- Now you can use the Run button to debug RDM (Breakpoints etc. also work)
