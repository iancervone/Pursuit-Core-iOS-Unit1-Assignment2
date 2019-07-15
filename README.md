## Unit 1 Hangman

import Foundation


let allTheWords = ["able", "about", "account", "acid", "across", "addition", "adjustment", "advertisement", "after", "again", "against", "agreement", "almost", "among", "amount", "amusement", "angle", "angry", "animal", "answer", "apparatus", "apple", "approval", "arch", "argument", "army", "attack", "attempt", "attention", "attraction", "authority", "automatic", "awake", "baby", "back", "balance", "ball", "band", "base", "basin", "basket", "bath", "beautiful", "because", "before", "behaviour", "belief", "bell", "bent", "berry", "between", "bird", "birth", "bite", "bitter", "black", "blade", "blood", "blow", "blue", "board", "boat", "body", "boiling", "bone", "book", "boot", "bottle", "brain", "brake", "branch", "brass", "bread", "breath", "brick", "bridge", "bright", "broken", "brother", "brown", "brush", "bucket", "building", "bulb", "burn", "burst", "business", "butter", "button", "cake", "camera", "canvas", "card", "care", "carriage", "cart", "cause", "certain", "chain", "chalk", "chance", "change", "cheap", "cheese", "chemical", "chest", "chief", "chin", "church", "circle", "clean", "clear", "clock", "cloth", "cloud", "coal", "coat", "cold", "collar", "colour", "comb", "come", "comfort", "committee", "common", "company", "comparison", "competition", "complete", "complex", "condition", "connection", "conscious", "control", "cook", "copper", "copy", "cord", "cork", "cotton", "cough", "country", "cover", "crack", "credit", "crime", "cruel", "crush", "current", "curtain", "curve", "cushion", "damage", "danger", "dark", "daughter", "dead", "dear", "death", "debt", "decision", "deep", "degree", "delicate", "dependent", "design", "desire", "destruction", "detail", "development", "different", "digestion", "direction", "dirty", "discovery", "discussion", "disease", "disgust", "distance", "distribution", "division", "door", "doubt", "down", "drain", "drawer", "dress", "drink", "driving", "drop", "dust", "early", "earth", "east", "edge", "education", "effect", "elastic", "electric", "engine", "enough", "equal", "error", "even", "event", "ever", "every", "example", "exchange", "existence", "expansion", "experience", "expert", "face", "fact", "fall", "false", "family", "farm", "father", "fear", "feather", "feeble", "feeling", "female", "fertile", "fiction", "field", "fight", "finger", "fire", "first", "fish", "fixed", "flag", "flame", "flat", "flight", "floor", "flower", "fold", "food", "foolish", "foot", "force", "fork", "form", "forward", "fowl", "frame", "free", "frequent", "friend", "from", "front", "fruit", "full", "future", "garden", "general", "girl", "give", "glass", "glove", "goat", "gold", "good", "government", "grain", "grass", "great", "green", "grey", "grip", "group", "growth", "guide", "hair", "hammer", "hand", "hanging", "happy", "harbour", "hard", "harmony", "hate", "have", "head", "healthy", "hear", "hearing", "heart", "heat", "help", "high", "history", "hole", "hollow", "hook", "hope", "horn", "horse", "hospital", "hour", "house", "humour", "idea", "important", "impulse", "increase", "industry", "insect", "instrument", "insurance", "interest", "invention", "iron", "island", "jelly", "jewel", "join", "journey", "judge", "jump", "keep", "kettle", "kick", "kind", "kiss", "knee", "knife", "knot", "knowledge", "land", "language", "last", "late", "laugh", "lead", "leaf", "learning", "leather", "left", "letter", "level", "library", "lift", "light", "like", "limit", "line", "linen", "liquid", "list", "little", "living", "lock", "long", "look", "loose", "loss", "loud", "love", "machine", "make", "male", "manager", "mark", "market", "married", "mass", "match", "material", "meal", "measure", "meat", "medical", "meeting", "memory", "metal", "middle", "military", "milk", "mind", "mine", "minute", "mist", "mixed", "money", "monkey", "month", "moon", "morning", "mother", "motion", "mountain", "mouth", "move", "much", "muscle", "music", "nail", "name", "narrow", "nation", "natural", "near", "necessary", "neck", "need", "needle", "nerve", "news", "night", "noise", "normal", "north", "nose", "note", "number", "observation", "offer", "office", "only", "open", "operation", "opinion", "opposite", "orange", "order", "organization", "ornament", "other", "oven", "over", "owner", "page", "pain", "paint", "paper", "parallel", "parcel", "part", "past", "paste", "payment", "peace", "pencil", "person", "physical", "picture", "pipe", "place", "plane", "plant", "plate", "play", "please", "pleasure", "plough", "pocket", "point", "poison", "polish", "political", "poor", "porter", "position", "possible", "potato", "powder", "power", "present", "price", "print", "prison", "private", "probable", "process", "produce", "profit", "property", "prose", "protest", "public", "pull", "pump", "punishment", "purpose", "push", "quality", "question", "quick", "quiet", "quite", "rail", "rain", "range", "rate", "reaction", "reading", "ready", "reason", "receipt", "record", "regret", "regular", "relation", "religion", "representative", "request", "respect", "responsible", "rest", "reward", "rhythm", "rice", "right", "ring", "river", "road", "roll", "roof", "room", "root", "rough", "round", "rule", "safe", "sail", "salt", "same", "sand", "scale", "school", "science", "scissors", "screw", "seat", "second", "secret", "secretary", "seed", "seem", "selection", "self", "send", "sense", "separate", "serious", "servant", "shade", "shake", "shame", "sharp", "sheep", "shelf", "ship", "shirt", "shock", "shoe", "short", "shut", "side", "sign", "silk", "silver", "simple", "sister", "size", "skin", "skirt", "sleep", "slip", "slope", "slow", "small", "smash", "smell", "smile", "smoke", "smooth", "snake", "sneeze", "snow", "soap", "society", "sock", "soft", "solid", "some", "song", "sort", "sound", "soup", "south", "space", "spade", "special", "sponge", "spoon", "spring", "square", "stage", "stamp", "star", "start", "statement", "station", "steam", "steel", "stem", "step", "stick", "sticky", "stiff", "still", "stitch", "stocking", "stomach", "stone", "stop", "store", "story", "straight", "strange", "street", "stretch", "strong", "structure", "substance", "such", "sudden", "sugar", "suggestion", "summer", "support", "surprise", "sweet", "swim", "system", "table", "tail", "take", "talk", "tall", "taste", "teaching", "tendency", "test", "than", "that", "then", "theory", "there", "thick", "thin", "thing", "this", "thought", "thread", "throat", "through", "through", "thumb", "thunder", "ticket", "tight", "till", "time", "tired", "together", "tomorrow", "tongue", "tooth", "touch", "town", "trade", "train", "transport", "tray", "tree", "trick", "trouble", "trousers", "true", "turn", "twist", "umbrella", "under", "unit", "value", "verse", "very", "vessel", "view", "violent", "voice", "waiting", "walk", "wall", "warm", "wash", "waste", "watch", "water", "wave", "weather", "week", "weight", "well", "west", "wheel", "when", "where", "while", "whip", "whistle", "white", "wide", "will", "wind", "window", "wine", "wing", "winter", "wire", "wise", "with", "woman", "wood", "wool", "word", "work", "worm", "wound", "writing", "wrong", "year", "yellow", "yesterday", "young"]




//the code below works to choose a word from "allTheWords", then turn that word into an array saved as "letters", then hide each of those characters as white spaces in "hiddenWord"
var answer = allTheWords.randomElement()!
print(answer)
var letters = Array(answer)
print(letters)
var hiddenWord = [Character]()
for _ in letters {
hiddenWord.append("_")
}
print(hiddenWord)





//below are the only inputs a user can make. if they enter any other value including nil then they will be told to guess again
let alphabet: Set<String> = ["a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"]

//the code below will check if the letter is within the word. If it is in the word then the user will be told they got a letter, if they guessed wrong and still have guess they will be told to try again otherwise the game is over. (I still need to show this letter in its place(s) within the word)
var guessLimit: Int = 8
var guessCount: Int = 0
var wrongGuesses = [Character]()
var guess: Character = "a"

for x in letters {
//    this is works to find a letter if the letter occurs only once in the word if it occurs more then that it does not work
if letters.contains(guess) {
let indexOfX = letters.index(of: guess)!
hiddenWord[indexOfX] = guess
print("you guessed a letter")
print(hiddenWord)
break
} else
if guessCount < guessLimit {
guessCount = guessCount + 1
wrongGuesses.append(guess)
print("wrong guesses = \(wrongGuesses)")
print("guess again")
} else
if guessCount == guessLimit {
print("game over")
}
}




////below is what happens if we change the letter and run the same block of code as above a second time with a different letter that IS IN THE ANSWER "letters"  This code works and needs t be turned into a function as a loop.
//guess = "t"
//if letters.contains(guess) {
//    let indexOfX = letters.index(of: guess)!
//    hiddenWord.insert(guess, at: indexOfX)
//    print("you guessed a letter")
//    print(hiddenWord)
//} else
//    if guessCount < guessLimit {
//        guessCount = guessCount + 1
//        wrongGuesses.append(guess)
//        print("wrong guesses = \(wrongGuesses)")
//        print("guess again")
//    } else
//        if guessCount == guessLimit {
//            print("game over")
//}
//
////below is what happens if we change the letter and run the same block of code as above a second time with a different letter that IS NOT IN THE ANSWER "letters"
//guess = "x"
//if letters.contains(guess) {
//    //    this is where we need to locate the index(s) of the letter guessed in "letters" and set tat letter to same index(s) in "hiddenWord
//    let indexOfX = letters.index(of: guess)!
//    hiddenWord.insert(guess, at: indexOfX)
//    print("you guessed a letter")
//    print(hiddenWord)
//} else
//    if guessCount < guessLimit {
//        guessCount = guessCount + 1
//        wrongGuesses.append(guess)
//        print("wrong guesses = \(wrongGuesses)")
//        print("guess again")
//    } else
//        if guessCount == guessLimit {
//            print("game over")
//}




//switch guess {
//case letters.0:
//    print("you got a letter")
//    }





//for x in letters {
//    hiddenWord(0) = x
//}




//func setWord(library: [String]) {
//    var answer = library.randomElement()!
//    var word = [0:"_", 1:"_", 2:"_", 3:"_", 4:"_", 5:"_"]
//    for letter in answer {
//        for value in
//        if let letter = word[] {
//            word[] = letter
//        }
//    }
//}

//setWord(library: allTheWords)
//
//for letter in answer {
//    if let letter = word[key] {
//    word[key] = letter = key
//    }
//}
//print(word)


//func setWord(word: String) {
//    var word = [Int:Character]()
//
//    for key in word {
//        if let currentLetter = word[key] {
//            word[key] = currentNum = key
//        }
//    }
//    print(dictOfStuff)
//    var mostFrequent = dictOfStuff.values.max()
//    if let mostFrequent = mostFrequent {
//        print(mostFrequent)
//    }
//}







//function for user to guess a letter
//1   user enters letter
//2   computer checks letter
//3a   if letter is correct show user where the letter appears in the hiddenWord along
//3b   if letter is wrong add 1 to guessCount
//4a   if hiddenWord has no more white spaces in it print: "you win"
//4b   if guessCount >= guessLiimit print: "you lose"
//4c   if neither 4a or 4b then print "guess again"




//for letter in word {
//    if guess = letter {
//
//    }
//}




