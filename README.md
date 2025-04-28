<p>Projet Elise - Araign&eacute;e Robotique</p>
<header>

	<h1 style="text-align: center;">Projet Elise : Araign&eacute;e Robotique</h1>
	<hr>
</header>
<section>

	<h2>Introduction</h2>

	<p>Bienvenue sur la pr&eacute;sentation de mon projet <strong>Elise</strong> ! L&#39;objectif est de construire une araign&eacute;e robotique capable de suivre un &eacute;metteur, en s&#39;inspirant du personnage &quot;Elise&quot; dans sa forme araign&eacute;e du jeu League of Legends.</p>
</section>
<section>

	<h2>Architecture du Projet</h2>

	<p>Le syst&egrave;me est bas&eacute; sur :</p>

	<ul>
		<li>Un microcontr&ocirc;leur pour piloter les moteurs (ESP32, STM32, etc.).</li>
		<li>Des moteurs DC avec r&eacute;ducteur et driver DRV8833 pour contr&ocirc;ler les pattes.</li>
		<li>Un syst&egrave;me de levage par vis-&eacute;crou adapt&eacute; aux mouvements verticaux.</li>
		<li>Des servomoteurs pour la synchronisation des articulations.&nbsp;<img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/patte%20num%C3%A9rotation.png" style="width: 300px;" class="fr-fic fr-dib"></li>
	</ul>
</section>

<p>Le mouvement rechercher est de faire avancer l&#39;araign&eacute;e, les pattes 1/2, 3/4,5/6 et 7/8 vont avancer et reculer sur le m&ecirc;me moteur, par exemple quand 1 avance, 2 recule forc&eacute;ment, cela permet d&#39;&eacute;conomiser 4 moteurs et beaucoup de place dans le corps de l&#39;araign&eacute;e. On joue donc sur la hauteur de la patte pour contr&ocirc;l&eacute; les mouvements de l&#39;araign&eacute;e, si la patte 2 est lev&eacute;e, et que 1 est baiss&eacute; et de m&ecirc;me pour les autres lignes de pattes, alors l&#39;araign&eacute;e avance. Si les deux pattes sont baiss&eacute;es, on effectue une rotation.</p>
<section>

	<h2>M&eacute;canique des Pattes</h2>

	<p>Chaque patte est control&eacute;e par des moteurs DC et un systeme d&#39;engrenage.</p>

	<p>On a voit ici une deuxi&egrave;me version d&#39;impression de la patte, la premi&egrave;re &eacute;tait moins &eacute;paisse dans le deuxi&egrave;me &quot;os&quot; de la patte et pr&eacute;sentait des dangers de r&eacute;sistance. La version derni&egrave;re version sur onshape a &eacute;galement corrig&eacute; le manque d&#39;un chamfer entre l&#39;engrenage et la patte qui ne permettait pas de couvrir l&#39;angle voulu pour tourner la patte d&#39;o&ugrave; le fait qu&#39;un bout a &eacute;t&eacute; coup&eacute; ici.</p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/photo_patte_ELISE.jpg" style="width: 300px;" class="fr-fic fr-dib">

	<p>
		<br>
	</p>

	<p>On voit ici l&#39;int&eacute;rieur du corps de l&#39;araign&eacute;e, la colonne d&#39;engrenage au milieu est la colonne motoris&eacute;e, lorsque l&#39;engrenage de la premi&egrave;re ligne tourne, dans le sens horaire par exemple, l&#39;engrenage 2 colonnes &agrave; gauche et &agrave; droite vont tourner dans le m&ecirc;me sens.</p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/corp__topview_ELISE.png" style="width: 300px;" class="fr-fic fr-dib">

	<p>La partie bleu est donc vis&eacute; (M2.5) aux engrenages qui se trouvent aux extr&eacute;mit&eacute;s (ceux ayant un deuxi&egrave;me trou excentr&eacute;) ainsi la rotation fait un effet levier sur les c&ocirc;tes de l&#39;araign&eacute;es qui maintiennent la patte (d&#39;o&ugrave; la n&eacute;cessit&eacute; du chamfer coup&eacute; &agrave; la main vu pr&eacute;c&eacute;demment). Ainsi la patte 1 va se reculer et la patte 2 va s&#39;avancer.</p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/joint_patte_corp_ELISE.png" style="width: 300px;" class="fr-fic fr-dib"><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/photo_engrenage_ELISE.jpg" style="width: 300px;" class="fr-fic fr-dib"></section>
<section>

	<h2>Electronique Embarqu&eacute;e</h2>

	<p>Le contr&ocirc;le est r&eacute;alis&eacute; via PWM pour la vitesse des moteurs et signaux GPIO pour la direction. Chaque moteur est g&eacute;r&eacute; ind&eacute;pendamment pour obtenir profiter du nombre de moteur pour la vari&eacute;t&eacute; de mouvement programmable possible.</p>

	<p>
		<br>
	</p>

	<p>Pour le sch&eacute;matique, on a la partie stm32g431.</p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847102192.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<p>
		<br>
	</p>

	<p>La partie driver des moteurs.</p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847159227.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<p>
		<br>
	</p>

	<p>Et les connecteurs (et mounting holes)</p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847201873.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<p>Pour le routage, j&#39;ai mis la partie stm sur le top et la partie driver sur le bottom avec un plan de 3V3 sous la partie stm et un plan 7V5 sur la partie driver. Cela donne cela :</p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847265233.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847291506.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<p>Et enfin le PCB :&nbsp;</p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847345473.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<p><img src="http://maker.coventgarden.fr/media/uploads/froala_editor/images/1745847360132.png" style="width: 300px;" class="fr-fic fr-dib"></p>

	<h2>Perspectives</h2>

	<p>Prochaines &eacute;tapes : int&eacute;gration d&#39;un syst&egrave;me de vision pour permettre &agrave; l&#39;araign&eacute;e de rep&eacute;rer dynamiquement l&#39;&eacute;metteur et adaptater sa trajectoire en temps r&eacute;el. Je n&#39;ai toutefois pas eu le temps de design cette partie qui n&#39;est donc pas inclus sur le PCB</p>
</section>
<footer>
	<hr>

	<p style="text-align: center;">Projet r&eacute;alis&eacute; par Victor Morel - Ann&eacute;e 2025</p>
</footer>

<p data-f-id="pbf" style="text-align: center; font-size: 14px; margin-top: 30px; opacity: 0.65; font-family: sans-serif;">Powered by <a href="https://www.froala.com/wysiwyg-editor?pb=1" title="Froala Editor">Froala Editor</a></p>
