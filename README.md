# NinjaModalView
Modal transition animation like the new 2018 AppStore.

![alt text](https://github.com/UzumakiAlfredo/NinjaModalView/blob/master/Preview.gif?raw=true)

I borrowd source file from [PaoloCuscela](https://github.com/PaoloCuscela/Cards)

# Installation
1. Copy Source.zip to you computer, exract it and add Source folder to your Project.
2. Create a simple tableView in your project & set prototype cells to 1 on storyboard.
3. set that prototype cell indentifire to "EmptyCell" like image below:
![alt text](https://github.com/UzumakiAlfredo/NinjaModalView/blob/master/CustomCell.png?raw=true)

4. The harderst part is to customize PageHeader class to your desired tableView cell.
        to do this, simply customize PageHeader class as you wish. this class is what you see on each tableView cell & the header of every detailed target cotroller you will push to.
5. Now you just need to implement your detail controller header in 'cellForRowAt' like this:

```
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "EmptyCell", for: indexPath)
        if let cellView = cell.viewWithTag(1000) as? PageHeader { 
            let cardContent = storyboard!.instantiateViewController(withIdentifier: "YourDetailViewController") as! YourDetailViewController // add any ViewController here
            cellView.shouldPresent(cardContent, from: self, fullscreen: true)
            cellView.backgroundImage = #imageLiteral(resourceName: "asian")
            cellView.title = "title: \(indexPath.row)"
            cellView.subtitle = "subtitle: \(indexPath.row)"
            cellView.shadowOpacity = 0.3
        } else {
            cell.textLabel?.text = "PageHeader Not Found"
        }
        return cell
    }
    ```
