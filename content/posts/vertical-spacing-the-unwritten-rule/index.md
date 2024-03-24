---
title: "Vertical Spacing & Reducing Cognitive Load"
date: 2024-03-24
description: "Vertical Spacing and the myth of readability."
draft: false
---
The lack of vertical spacing to be exact.

Like everything related to readability, you might argue it's a  __skill issue__. 
![Skill issue](skill-issue.jpeg)
Which I can accept, whilst shedding a tear, but that's a topic for another day though.

The cognitive load theory suggests that our working memory has a limited capacity for processing new information. When code is densely packed without clear visual breaks, it increases the cognitive load on developers trying to understand the code.

Logically grouping code by relating variables or patterns help build this mind map of how the code is working subconciously. By doing this and separating unrelated sections, developers can better understand the relationships and dependencies within the code.

Without realizing it, we start to process the code and its functions by visualizing it in one way or another. Not having clear breakpoints for closely related items slows this process. Vertical spacing reduces the cognitive effort required to parse and understand the code. It highlights the structure, making it less overwhelming for both new and experienced developers.

It's like a reading a book, you need paragraphs to group sentences and clearly break from the next set of ideas.

This example is only 18 lines long, so not a great example, but I feel it helps explain what I'm trying to get across.

```go
// No Spacing
func init() {
	configDir, err := os.UserConfigDir()
	viper.SetConfigName("config")
	viper.SetConfigType("toml")
	viper.AddConfigPath(fmt.Sprintf("%s/quicknote-ai", configDir))
	err = viper.ReadInConfig()
  	if err != nil {
		fmt.Println("Errored reading config:", err)
		return
	}
	if !viper.IsSet("openai_api_key") {
		fmt.Println("Please add your openai_api_key to the config")
		return
	}
	client := &http.Client{}
	aiService = ai.NewOpenAIService(viper.GetString("openai_api_key"), client)
	noteCmd.Flags().StringVarP(&thought, "thought", "t", "", "No thoughts wise guy?")
	noteCmd.MarkFlagRequired("thought")
	noteCmd.Flags().StringVarP(&model, "model", "m", "gpt-3.5-turbo", "Fancy a specific model?")
	rootCmd.AddCommand(noteCmd)
}

// Spacing
func init() {
	configDir, err := os.UserConfigDir()

	if err != nil {
		fmt.Println("Error getting config directory:", err)
		return
	}

	viper.SetConfigName("config")
	viper.SetConfigType("toml")
	viper.AddConfigPath(fmt.Sprintf("%s/quicknote-ai", configDir))

	err = viper.ReadInConfig()

	if err != nil {
		fmt.Println("Errored reading config:", err)
		return
	}

	if !viper.IsSet("openai_api_key") {
		fmt.Println("Please add your openai_api_key to the config")
		return
	}

	client := &http.Client{}
	aiService = ai.NewOpenAIService(viper.GetString("openai_api_key"), client)

	noteCmd.Flags().StringVarP(&thought, "thought", "t", "", "No thoughts wise guy?")
	noteCmd.MarkFlagRequired("thought")
	noteCmd.Flags().StringVarP(&model, "model", "m", "gpt-3.5-turbo", "Fancy a specific model?")

	rootCmd.AddCommand(noteCmd)
}
```

There's a practical article with multiple examples in python of this in an article I've often referred people too in the past [here](https://www.staycaffeinated.com/2020/05/27/coding-standards-whitespace), it's a good read.
