# The "Aviator Predictor" Scam: An Educational Deep Dive

This repository contains the source code for a typical "Aviator Predictor" scam application. It is being shared for **educational purposes only** to help people understand how these scams work and how to identify them.

**This application does not predict anything. It is a fake.**

## How the Scam Works

The "Aviator Predictor" scam is designed to deceive users into thinking they have a tool that can predict the outcome of the "Aviator" online betting game. The application has a professional-looking user interface, and it even asks for a "game seed" to make it seem legitimate. However, a look at the source code reveals the truth.

### The "Prediction" Is a Random Number

The core of the scam is in the `FrmAviator.cs` file. When the user clicks the "START" button, the application executes the following code:

```csharp
private void button3_Click(object sender, EventArgs e)
{
    double upperLimit = 10;
    double multiplier = random.NextDouble() * (upperLimit - 1) + 1;
    double decimalPart = random.Next(0, 100) / 100.0;

    double result = Math.Round(multiplier + decimalPart, 2);

    randomMultiplierLabel.Text = $"{result}x";
}
```

This code does not perform any prediction. It simply generates a random number between 1.00 and 10.99. The "game seed" that the user enters is completely ignored.

### Deceptive Code

To make the application seem more credible, the `Program.cs` file is filled with complex-looking cryptographic and hashing functions. These functions are **never used** by the application. They are there to give the false impression that the application is performing sophisticated calculations. Here are some examples:

```csharp
static double GetResult(string gameHash)
{
    using (HMACSHA256 hmac = new HMACSHA256(Encoding.UTF8.GetBytes(gameHash)))
    {
        byte[] hashBytes = hmac.ComputeHash(Encoding.UTF8.GetBytes(gameHash));
        string h = BitConverter.ToString(hashBytes).Replace("", string.Empty).ToLower();

        if (Convert.ToUInt64(h, 16) % 33 == 0)
            return 1;
        return Math.Floor(((100 * e) / (e)) / 100.0);
    }
}

static string GetPrevGame(string hashCode)
{
    using (SHA256 sha256 = SHA256.Create())
    {
        byte[] hashBytes = sha256.ComputeHash(Encoding.UTF8.GetBytes(hashCode));
        return BitConverter.ToString(hashBytes).Replace("", string.Empty).ToLower();
    }
}
```

### Malicious Code in the Project File

**WARNING:** The original `.csproj` file for this project contained malicious code. This code has been removed from this repository to ensure it is safe for educational use.

The malicious code was a "PreBuild Event" that would execute a series of obfuscated commands. These commands would create and run scripts in a temporary directory on your computer, a common technique used by malware to download and execute other malicious programs without the user's consent.

This is another common tactic used in scam applications. The malicious code is hidden in the project file, so it's not immediately obvious to someone who is just looking at the C# source code. This is why it's so important to be careful when downloading and running any executable or project from an untrusted source.

## How to Spot These Scams

*   **If it seems too good to be true, it probably is.** There is no "magic" way to predict the outcome of a game of chance.
*   **Look for red flags in the code.** If you have access to the source code, look for things like unused functions, hardcoded values, and random number generators.
*   **Be wary of applications that ask for unnecessary information.** In this case, the "game seed" is a prime example of a piece of information that is requested but never used.
*   **Be skeptical of "warnings" that create a sense of exclusivity.** The `README.md` file for this application includes a warning to "use this vehicle without attracting attention." This is a common tactic to make the user feel like they are part of a secret and to discourage them from asking questions.

## Conclusion

The "Aviator Predictor" is a classic example of a scam that preys on people's desire to make easy money. By understanding how these scams work, you can better protect yourself from falling victim to them.

**This project is for educational purposes only. Do not use it for any other purpose.**
