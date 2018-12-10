This code will list all files within the directory that the source code is located in 

import Foundation

let files = FileManager.default
let path = Bundle.main.resourcePath!

let items = try files.contentsOfDirectory(atPath: path)
print("Files: ")
for i in items{
  print(i)
}
