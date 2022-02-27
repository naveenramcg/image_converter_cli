from click import style
import typer
from PIL import Image
from rich import console, table, markdown, progress
import time

console = console.Console()
app = typer.Typer()

#markdown
MARKDOWN = """# FUNCTIONS INCLUDED"""
md = markdown.Markdown(MARKDOWN)

#table
table = table.Table(title = "")
table.add_column("No.", style = "cyan")
table.add_column("Name", style = "magenta")
table.add_column("Function", style = "yellow")
table.add_column("Syntax", style = "green")

table.add_row("1", "image",  "To view the image", "python main.py image filename")
table.add_row("2", "resize", "To resize the image", "python main.py resize filename width height")
table.add_row("3", "changeformat",  "To change the file format to png or jpg", "python main.py fileformat filename")
console.print(md)
console.print(table)

@app.command()
def image(filename: str):
    typer.echo(f'opening {filename}\n')
    image1  = Image.open(f"{filename}")
    for i in progress.track(range(10), description="opening"):
        time.sleep(0.02)
    image1.show()
    console.print("\nIMAGE OPENED", style = "bold green")

@app.command()
def resize(filename: str, width:int, height: int):
    console.print(f"Resizing image to size({width}, {height})\n", style = "bold red")
    size = (height, width)
    image1  = Image.open(f"{filename}")
    image1.thumbnail(size)
    for i in progress.track(range(10), description="Resizing"):
        time.sleep(0.1)
    image1.save('resize_'+f"{filename}")
    console.print("\nCOMPLETED", style = "bold green")

@app.command()
def changeformat(filename: str):
    image1  = Image.open(f"{filename}")
    console.print("Converting image\n", style = "bold")
    name = filename[:-4]
    for i in progress.track(range(10), description="Converting"):
        time.sleep(0.03)
    if filename.endswith('.jpg'):
        image1.save(f"{name}.png")
        im = Image.open(f"{name}.png")
        im.show()
    elif filename.endswith('.png'):
        image1.save(f"{name}.jpg")
        im = Image.open(f"{name}.jpg")
        im.show()
    console.print("\nCOMPLETED CONVERSION", style = "bold green")

if __name__ == "__main__":
    app()
