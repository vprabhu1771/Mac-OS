//
//  CourseViewModel.swift
//  Backend
//
//  Created by mac_rig2 on 21/01/23.
//

import Foundation
import SwiftUI

struct CourseModel: Hashable, Codable {
    
    let name: String
    
    let image: String
    
}

class CourseViewModel: ObservableObject {
    
    @Published var courses: [CourseModel] = []
    
    func fetch() {
        
        guard let url = URL(string: "http://iosacademy.io/api/v1/courses/index.php") else
        {
            return
        }
        
        let task = URLSession.shared.dataTask(with: url) { [weak self] data, _, error in
            
            guard let data = data, error == nil else {
                return
            }
            
            // Convert To JSON
            do
            {
                let courses = try JSONDecoder().decode([CourseModel].self, from: data)
                
                DispatchQueue.main.async {
                    self?.courses = courses
                }
            }
            catch {
                print(error)
            }
        }
        
        
        task.resume()
    }
}
