# Text Style Transfer in Fiction

This is a companion repo to paper 'Style transfer in Fiction' that helps with experimenting with style in literature.
The main idea in this project is a brute force rejection-pass architecture that parses the content source for lexemes and uses a text generator (GPT-2) fine-tuned for the target style to generate many samples. If there are samples matching a given content lexeme in embedding, it is being replaced. Since replacement lexemes come from a distribution of style author, this achieves a style shift in the output text. 




