# Opdrachten

1. Welke queries bevat het schema?
2. Welke categorien zijn er?
3. Hoe vraag je het totaal aantal klanten op?
4. Schrijf een query om het totaal aantal klanten op en van alle klanten de naam en gebruikersnaam. 
   1. maakt het nog uit in welke volgorde je de elementen zet? 
5. Wat voor huisdier is "S-4"


"S-4
  query PetById($petByIdId: ID!) {
  petById(id: $petByIdId) {
    name
    category
    photo {
      thumb
    }   
    status
    weight
  }
}
{
  "petByIdId": "S-4"
}

query PetById {
  petById(id: "S-4") {
    name
    category
    photo {
      thumb
    }   
    status
    weight
  }
}

