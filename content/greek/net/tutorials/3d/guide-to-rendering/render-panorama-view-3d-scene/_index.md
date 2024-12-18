---
title: Αποδώστε μια πανοραμική προβολή μιας τρισδιάστατης σκηνής χρησιμοποιώντας το Aspose.3D για .NET
linktitle: Αποδώστε μια πανοραμική προβολή μιας τρισδιάστατης σκηνής
second_title: Aspose.3D .NET API
description: Μάθετε πώς να αποδίδετε μια εκπληκτική πανοραμική προβολή μιας τρισδιάστατης σκηνής στις εφαρμογές σας .NET χρησιμοποιώντας το Aspose.3D. Ακολουθήστε τον βήμα προς βήμα οδηγό μας για καθηλωτική απόδοση σκηνής.
type: docs
weight: 13
url: /el/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Εισαγωγή

Η δημιουργία καθηλωτικών, πανοραμικών σκηνών 3D αλλάζει το παιχνίδι για προγραμματιστές που θέλουν να βελτιώσουν τις εφαρμογές τους με εκπληκτικά οπτικά εφέ. Είτε εργάζεστε σε μηχανή παιχνιδιών, αρχιτεκτονική οπτικοποίηση ή καθηλωτικές εμπειρίες ιστού, η απόδοση τρισδιάστατων σκηνών ως πανοράματα επιτρέπει στους χρήστες να βιώνουν μια δυναμική προβολή από όλες τις γωνίες. Το Aspose.3D for .NET είναι το τέλειο εργαλείο για την απρόσκοπτη ενσωμάτωση αυτής της δυνατότητας στα έργα σας .NET. Αυτός ο περιεκτικός οδηγός θα σας καθοδηγήσει στη διαδικασία απόδοσης ενός πανοράματος από μια τρισδιάστατη σκηνή χρησιμοποιώντας το Aspose.3D για .NET.

## Προαπαιτούμενα

Πριν ξεκινήσετε τη διαδικασία απόδοσης, βεβαιωθείτε ότι έχετε τα εξής:

- Aspose.3D για .NET: Για να ξεκινήσετε, πρέπει να εγκαταστήσετε το Aspose.3D, το οποίο παρέχει όλα τα απαραίτητα εργαλεία για το χειρισμό τρισδιάστατων στοιχείων και την απόδοση.[Κατεβάστε το Aspose.3D για .NET](https://releases.aspose.com/3d/net/) για να ξεκινήσετε.
- .NET Development Environment: Απαιτείται ένα πλήρως διαμορφωμένο περιβάλλον ανάπτυξης .NET. Βεβαιωθείτε ότι έχετε Visual Studio ή οποιοδήποτε άλλο συμβατό IDE.
-  Δείγμα αρχείου 3D σκηνής: Μπορείτε να χρησιμοποιήσετε οποιαδήποτε τρισδιάστατη σκηνή σε μορφές όπως`.glb`, `.fbx` , ή`.obj`. Για αυτό το σεμινάριο, θα χρησιμοποιήσουμε ένα απλό αρχείο "VirtualCity.glb".

Αφού καλύψετε αυτές τις προϋποθέσεις, μπορούμε να προχωρήσουμε στο στήσιμο της σκηνής.

## Εισαγωγή απαραίτητων χώρων ονομάτων

Για εργασία με το Aspose.3D, θα χρειαστεί να εισαγάγουμε αρκετούς χώρους ονομάτων στο έργο μας. Αυτοί οι χώροι ονομάτων σάς επιτρέπουν να χειρίζεστε αποτελεσματικά τρισδιάστατα αντικείμενα, ρυθμίσεις κάμερας και επιλογές απόδοσης.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Αυτοί οι χώροι ονομάτων είναι απαραίτητοι για τη φόρτωση της τρισδιάστατης σκηνής, τη διαμόρφωση της κάμερας, το φωτισμό και τη ρύθμιση των υφών απόδοσης που σχηματίζουν την πανοραμική προβολή.

## Βήμα 1: Φορτώστε την τρισδιάστατη σκηνή στην εφαρμογή σας

 Το πρώτο βήμα είναι να φορτώσετε την τρισδιάστατη σκηνή στην εφαρμογή σας. Αυτό μπορεί να επιτευχθεί χρησιμοποιώντας το`Scene` τάξη που παρέχεται από την Aspose.3D. Αντικαθιστώ`"VirtualCity.glb"` με τη διαδρομή προς το αρχείο τρισδιάστατης σκηνής.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 Ο`Scene` Το αντικείμενο φορτώνει την τρισδιάστατη σκηνή στη μνήμη, επιτρέποντάς σας να αλληλεπιδράσετε μαζί της και να εφαρμόσετε τεχνικές απόδοσης.

## Βήμα 2: Ρυθμίστε την κάμερα και τα φώτα

Για να διασφαλίσετε ότι η τρισδιάστατη σκηνή σας αποτυπώνεται σωστά, θα χρειαστεί να ρυθμίσετε μια κάμερα και κατάλληλο φωτισμό. Η κάμερα σάς επιτρέπει να ελέγχετε την προοπτική της σκηνής, ενώ τα φώτα βοηθούν στον φωτισμό των αντικειμένων.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Ρύθμιση κάμερας: Το κοντινό και το μακρινό επίπεδο της κάμερας έχουν ρυθμιστεί να ορίζουν το ορατό εύρος στη σκηνή 3D.
- Ρύθμιση φωτός: Προστίθενται δύο φώτα—ένα φωτεινό σημείο και ένα άλλο με συγκεκριμένο χρώμα για να προσθέσετε βάθος και ρεαλισμό στη σκηνή.

## Βήμα 3: Ρυθμίστε το Renderer και καθορίστε τους στόχους Render

Τώρα που η σκηνή, η κάμερα και τα φώτα σας έχουν ρυθμιστεί, το επόμενο βήμα είναι να δημιουργήσετε το renderer και να ορίσετε τους στόχους απόδοσης. Ο renderer είναι υπεύθυνος για τη δημιουργία των τρισδιάστατων εικόνων και οι στόχοι απόδοσης καθορίζουν πού θα αποθηκευτεί η τελική έξοδος.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Cube Render Texture: Χρησιμοποιείται για την απόδοση ενός χάρτη κύβου για την πανοραμική προβολή. Ορίζουμε μια υφή 512x512 εδώ.
- Υφή τελικής απόδοσης: Αυτή είναι η υφή που θα κρατήσει την τελική ισοορθογώνια πανοραμική προβολή.

## Βήμα 4: Διαμορφώστε το Viewport και Render the Scene

Αφού δημιουργήσουμε τις υφές απόδοσης, πρέπει να διαμορφώσουμε τη θύρα προβολής, η οποία ορίζει την περιοχή της τρισδιάστατης σκηνής που θα καταγράψει η κάμερα.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Αυτός ο κώδικας ορίζει τη θύρα προβολής για τον χάρτη κύβου και αποδίδει τη σκηνή στο`rt` αποδίδουν υφή.

## Βήμα 5: Εφαρμογή Μετα-επεξεργασίας για Ισογραμμή προβολή

Σε αυτό το σημείο, πρέπει να εφαρμόσουμε μετα-επεξεργασία για να μετατρέψουμε τον χάρτη του κύβου σε μια ισόγεια πανοραμική προβολή. Αυτή η μεταμόρφωση διασφαλίζει ότι η τελική εικόνα θα είναι ένα σωστό πανόραμα.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Equirectangular Projection: Αυτό το εφέ μετα-επεξεργασίας παίρνει τον κύβο χάρτη και τον μετατρέπει σε ισοτεθογώνια πανοραμική προβολή, παρέχοντας απρόσκοπτη προβολή 360 μοιρών.

## Βήμα 6: Αποθηκεύστε το Rendered Panorama

Μόλις ολοκληρωθεί η απόδοση και η μετα-επεξεργασία, το τελευταίο βήμα είναι να αποθηκεύσετε το τελικό πανόραμα σε ένα αρχείο εικόνας, όπως ένα PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Αυτό αποθηκεύει την πανοραμική εικόνα στον καθορισμένο κατάλογο, επιτρέποντάς την να την ενσωματώσετε στην εφαρμογή σας ή να την εμφανίσετε σε έναν ιστότοπο.

## Σύναψη

Η απόδοση πανοραμικών προβολών τρισδιάστατων σκηνών δεν ήταν ποτέ ευκολότερη με το Aspose.3D για .NET. Ακολουθώντας τα βήματα που περιγράφονται παραπάνω, μπορείτε εύκολα να φορτώσετε μια τρισδιάστατη σκηνή, να διαμορφώσετε την κάμερα και τα φώτα, να αποδώσετε τη σκηνή και να εφαρμόσετε εφέ μετα-επεξεργασίας για να δημιουργήσετε καθηλωτικές πανοραμικές εικόνες. Το Aspose.3D for .NET παρέχει τη δύναμη και την ευελιξία για να ζωντανέψετε τις 3D απεικονίσεις σας και να τις ενσωματώσετε απρόσκοπτα στις εφαρμογές σας.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω τη δική μου τρισδιάστατη σκηνή για την απόδοση πανοράματος;
Απολύτως. Απλώς αντικαταστήστε τη διαδρομή του αρχείου σκηνής δείγματος με τη θέση της προσαρμοσμένης τρισδιάστατης σκηνής σας.

### Υπάρχουν διαθέσιμα πρόσθετα εφέ μετά την επεξεργασία;
Ναι, το Aspose.3D προσφέρει μια σειρά από εφέ μετα-επεξεργασίας, όπως βάθος πεδίου, άνθιση και πολλά άλλα, που μπορούν να εφαρμοστούν για τη βελτίωση των αποδιδόμενων εικόνων σας.

### Πώς μπορώ να βελτιστοποιήσω την απόδοση απόδοσης;
Η απόδοση της απόδοσης μπορεί να βελτιστοποιηθεί προσαρμόζοντας παραμέτρους όπως το μέγεθος και την ανάλυση της υφής της απόδοσης, καθώς και τροποποιώντας τα κοντινά και μακρινά επίπεδα της κάμερας.

### Μπορώ να το ενσωματώσω σε μια διαδικτυακή εφαρμογή;
Ναι, το Aspose.3D for .NET μπορεί να ενσωματωθεί στις εφαρμογές ιστού σας .NET για δυναμική απόδοση πανοράματος 3D.

### Υπάρχει κάποιο φόρουμ κοινότητας για υποστήριξη Aspose.3D;
 Ναι, μπορείτε να επισκεφθείτε το[Aspose.3D φόρουμ](https://forum.aspose.com/c/3d/18) για υποστήριξη και κοινοτικές συζητήσεις.