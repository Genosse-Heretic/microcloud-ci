-  Der erste Push nach einfuegen der compose.yml und /html ordner schlägt fehl, da im Test erwartet wird, dass Port 8085 offen ist und es wird derzeit noch 8081:80 geöffnet.


1.
- Jeder Push
- Pull Request auf "main"
- workflow dispatch als eigener Button

2. ubuntu-latest als Runner bereitgestellt von github

3. stack-test: 10 steps

4. step 1 : uses
steps 2,3,4,5,6,7,8,9,10  : run

5. read-only
Mehr Rechte braucht er nicht und es gilt das least-privilege Prinzip. Man geht weniger Risiko ein.

6. 
Wenn das Repo keine Template ist, wie unsere Repo, wird die Pipeline auf dem Ubuntu-latest runner ausgeführt.
Im Template selbst wird es nicht ausgeführt.

7.
i.  Step 3, da die Syntax-Prüfung fehlschlägt
ii. Step 7, index.html fehlt -> exit mit error
iii. Step 6, da der webserver im Container nicht standardmäßig auf port 8080 läuft und somit nicht erreicht wird
iv. Step 2, weil die Bedingung nicht rekursiv sucht und die Datei nicht findet

8. Weil sonst auch einfach eine Standardseite serviert werden könnte. Mit dem Diff-Check wird sichergestellt, dass die korrekte html bereitgestellt wird.

9. Der Container wird ordentlich beendet. Es wäre nicht zwingend notwendig, aber ist sauberer.

10. Es handelt sich um Continuous Integration. Der Code wird lediglich in seiner Funktionalität geprüft. Er wird nicht für Deployment vorbereitet oder direkt in einer Umgebung deployed.

11. 
- Automatisierung
- Standardisierung der Tests

12. Weil DOD 3 explizit das dev-branch prüft und der WOrkflow muss nicht laufen wenn nicht auf dev gepushed wird.
Es ist mit ?branch=dev eingebunden, da sonst der status des Workflows aus dem main-branch angezeigt werden würde, wo dieser ja gar nicht läuft.

13. Der merge muss durchgeführt worden sein vom dev-branch: merged_at head.ref
ebenso die NR und der sha hash vom Pull Request.
Die .conclusion vom Merge muss ein success gewesen sein.
