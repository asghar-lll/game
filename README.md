import { useState } from "react"; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card";

const questions = [ "Will you forgive me if I forget your birthday?", "Will you forgive me if I was rude to you?", "Do I deserve a second chance?", "Will you still talk to me if I disappear for a while?", "Can I say sorry without explaining everything?", "Would you forgive me if I lied once?", "Will you accept my apology even if it's late?", "Can we start over again?", "Will you forgive me if I broke your trust?", "Can I fix things between us?" ];

export default function MaafiGame() { const [index, setIndex] = useState(0); const [score, setScore] = useState(0); const [finished, setFinished] = useState(false);

const handleAnswer = (answer) => { if (answer === "yes") setScore(score + 1); if (index + 1 < questions.length) { setIndex(index + 1); } else { setFinished(true); } };

return ( <div className="flex flex-col items-center justify-center min-h-screen bg-gradient-to-b from-gray-100 to-gray-300 p-4"> <h1 className="text-3xl font-bold mb-4">Maafi Game</h1> {finished ? ( <Card className="p-6 text-center"> <CardContent> <p className="text-xl font-semibold">You gave {score} forgiveness{score !== 1 && "s"}!</p> </CardContent> </Card> ) : ( <Card className="max-w-md w-full p-6"> <CardContent> <p className="text-lg mb-6">{questions[index]}</p> <div className="flex justify-between"> <Button onClick={() => handleAnswer("yes")} className="bg-green-500 hover:bg-green-600">Yes</Button> <Button onClick={() => handleAnswer("no")} className="bg-red-500 hover:bg-red-600">No</Button> </div> </CardContent> </Card> )} </div> ); }

