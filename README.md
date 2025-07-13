import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";

export default function CharacterCreator() {
  const [character, setCharacter] = useState({
    name: "",
    age: "",
    role: "",
    traits: "",
    backstory: ""
  });

  const [savedCharacters, setSavedCharacters] = useState([]);

  const handleChange = (e) => {
    setCharacter({ ...character, [e.target.name]: e.target.value });
  };

  const handleSave = () => {
    setSavedCharacters([...savedCharacters, character]);
    setCharacter({ name: "", age: "", role: "", traits: "", backstory: "" });
  };

  return (
    <div className="p-4 max-w-2xl mx-auto">
      <h1 className="text-2xl font-bold mb-4">Create a Character</h1>

      <div className="space-y-2">
        <Input
          placeholder="Character Name"
          name="name"
          value={character.name}
          onChange={handleChange}
        />
        <Input
          placeholder="Age"
          name="age"
          value={character.age}
          onChange={handleChange}
        />
        <Input
          placeholder="Role (e.g. Protagonist, Villain)"
          name="role"
          value={character.role}
          onChange={handleChange}
        />
        <Textarea
          placeholder="Key Traits (e.g. Brave, Sarcastic)"
          name="traits"
          value={character.traits}
          onChange={handleChange}
        />
        <Textarea
          placeholder="Backstory"
          name="backstory"
          value={character.backstory}
          onChange={handleChange}
        />
        <Button onClick={handleSave}>Save Character</Button>
      </div>

      <div className="mt-8">
        <h2 className="text-xl font-semibold mb-2">Saved Characters</h2>
        <div className="grid gap-4">
          {savedCharacters.map((char, index) => (
            <Card key={index}>
              <CardContent className="p-4">
                <h3 className="text-lg font-bold">{char.name}</h3>
                <p><strong>Age:</strong> {char.age}</p>
                <p><strong>Role:</strong> {char.role}</p>
                <p><strong>Traits:</strong> {char.traits}</p>
                <p><strong>Backstory:</strong> {char.backstory}</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </div>
    </div>
  );
}
